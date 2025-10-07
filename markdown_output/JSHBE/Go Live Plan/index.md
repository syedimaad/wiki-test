### Population of Meta/Stats Table

#### Current Status

1.  Event from client is being processed by Lambda

2.  Lambda applies certain aggregations and algorithms and stores the
    data into Redis

3.  Every 5 mins one job is triggered to push the data to Dynamo via
    Lambda

4.  The updates in dynamo are of 2 types

    1.  Counter Update

    2.  Replace

5.  For populating in obelix we have added a step in lambda to send both
    counter and update values to kafka

6.  Updates in Dynamo DB are propagated to Elastic Search via a DDB
    trigger.

7.  For cold store update we are sending event to kafka topic, same is
    being listened by another Lambda which would be updating the data in
    ES

#### Go Live Challenges

1.  Dynamo DB trigger is currently updating the data in ES, the parallel
    process should be writting to the new ES

2.  Since there are counters present in the dynamo DB schema. Lifting
    and shifting the data while live updates are coming would cause data
    incostincency.

#### Proposed Steps for Go live

1.  Populate the cold store for content. -\>Done

2.  Create a lambda to consume from DDB trigger for stats with strict
    check on update if exists based on content uuid. This insert into
    Obelix ignores the counter and always replaces the data. -\>Done -
    (Test for Production-\>pendding)

3.  Setup a parallel ES for warm content only. -\>(IN_PROGRESS)

4.  Populate the Warm ES/Obelix Meta data.

    1.  Add kafka consumer in API to populate content meta data only in
        new ES/Obelix for a given content uuid.

    2.  Clean the current obelix.

    3.  Identify the warm content from current ES.

    4.  Restart the current create/update content pipeline running for
        new/exisitng content in obelix/warm ES.

    5.  Start populating the content meta data in new ES/Obelix from
        API/Ingester for Meta.

5.  Now that the meta tables are populated into Obelix, start the DDB
    trigger for stats table consumption for populating stats in warm
    ES/Obelix.

6.  To ensure all the contents are processed once, modify one attribute
    for each content uuid in dynamo. This would trigger the DDB trigger.

7.  Once all the data is 98% processed from the DDB trigger. We need to
    pause the reactions lambda for the rest of the data to be processed.
    This would ensure that the DDB triggers are stopped. Once the lag is
    cleared. Stop reading from the DDB trigger on the ingester.

    1.  Expected downtime for stoppage of reactions lambda \~15 mins.

8.  Now we need to enable the consumption from the update stats trigger
    in Obelix Ingester. For this we need to start the lambda.

9.  Monitor the data in Obelix and Dynamo for a week.

10. Decommission writting to Dynamo.
