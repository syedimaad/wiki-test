## Running Spark Jobs on Blaze cluster

1.  Install 0.3.0+ version of blazectl `pip install blazectl==0.3.0`

2.  Create a new cluster using blazectl tool. Now cluster creation
    requires the platform as an arg - tf or torch.

3.  Checkout `mtl-training-pipeline code` to branch:
    `shail_pyspark_2022_11_18`

4.  See example pyspark code in
    `dummy_trainer/mtl_pyspark_data_reader.py`

5.  Modify `main.py` to invoke the execute method.

**Next steps:**

1.  Abstract out PysparkDataLoader for independent run and trainer run.

2.  Independent run - Extend PysparkDataLoader for custom pipeline and
    integrate it to be invoked from main.py. Also add `spark` as
    platform to blazectl tool - we would not need Torch or TF
    dependencies when the intent is to run only spark jobs.

3.  Trainer run - implement Data Loader strategy that uses PySpark data
    reader to read data for the trainer.

4.  Benchmark - benchmark PySpark data loading speed vs. basic or async
    data loader for pre-joined data.
