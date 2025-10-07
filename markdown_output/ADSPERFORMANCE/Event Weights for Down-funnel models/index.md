#### App Event Weights

Sheet Link -
[[app_event_weights]{.underline}](https://docs.google.com/spreadsheets/u/0/d/1b8FWx2OvshIoA-QFSpq55_ZOOwBQtjbib-7gn1QjfAw/edit)

Steps for changing weights and including/excluding events - 

1.  Changing **is_updated** column value to 1 will make the model use
    manual_weight for downfunnel events.

2.  **By default** **manual_weight** is set to data driven
    **event_weight**. To use the default weight, only modify
    **is_updated to 1** (manual_weight should be equal to event_weight).

3.  To assign weights manually, **change manual_weight judiciously** and
    **is_updated to 1.**

4.  To **skip/stop downfunnel weights** training (all events are
    weighted equal), set **is_updated to 0.**

5.  Finally, To **exclude a particular event** from training (and its
    postbacks from being considered), set **is_positive to 0.**

6.  Changes will reflect in next day\'s model, or if needed, please run
    the following on VM - 

    1.  #dh-hw-ads-learning-n3.dailyhunt.in , directory -
        /grid/1/dh-ads  bin/run.sh
        AdLearning/src/main/python/entity_event_weights.py

        Changes are done in the table once the down funnel mail is
        received.

#### **App Event Mappings** 

Sheet Link -
[[event_mappings_sheet]{.underline}](https://docs.google.com/spreadsheets/d/1o_Om01S5L0gAJrt0-IByYIJdjH01mgsn9JboAX86abM/edit?usp=sharing)

To make changes to mappings, following are the guidelines -

1.  Mappings are **used to combine the postbacks** of two events, their
    weights will be adjusted accordingly

2.  Verify the childKey event that needs to be substituted for a
    parentKey event.

3.  **Paste the childKey** that should replace the other childKeys
    **into their respective parentKey cells.**

4.  Mappings will be updated everyday, or once the
    *entity_event_weights* script mentioned above is run.
