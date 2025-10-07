How to reset model weights and the timing before rerunning a model:

There are existing code snippets as part of Unit Test in\
`feature-processor`-\> `JobPipeLineFunctionTest.java` file which can be
leveraged for the purpose.\
\
For Resetting the Time, we need the find the last completed job and
reset the lastmodified date

For that we get the last job id using
`jobPipeLineFunction.getLastCompletedTrainingJobDetails(...)` and update
the time using
`jobPipeLineFunction.resetLastestTrainingJobModificationDate(...)`

This is the code snippet that does the resetting.

\@org.junit.Test public void resetModificationDate() throws
ParseException { SimpleDateFormat sdf = new
SimpleDateFormat(\"yyyy-MM-dd hh:mm\"); Date date =
sdf.parse(\"2022-04-20 15:00\"); System.out.println(date.getTime());
String platform=\"SPARK\"; String language=\"HI\"; String
model=\"JPLR21\"; TrainingJob trainingJob =
jobPipeLineFunction.getLastCompletedTrainingJobDetails(platform,language,model);
System.out.println(trainingJob);
System.out.println(trainingJob.getFileModificationDate());
System.out.println(\"Id: \" + trainingJob.getTrainingJobId());
jobPipeLineFunction.resetLastestTrainingJobModificationDate(platform,language,model,
trainingJob.getTrainingJobId(), date.getTime()); }

For Resetting the model weights we need to get the job id using
`jobPipeLineFunction.checkAndGetTrainingDetailsForEvalPipeline(...)`

And delete the `modelFile` and the `pmmlFile` stored for the job in
dynamoDB, such that when the training job tries to pick it up for next
job it get's `null` and reinitializes the weights to zero.

Once done
`TrainingJob trainingJob = jobPipeLineFunction.checkAndGetTrainingDetailsForEvalPipeline(...)`
can be used again to validate if the `modelPath` and the `pmmFilePath`
are `null`.

Once these are done the model weight & the timing are reset.
