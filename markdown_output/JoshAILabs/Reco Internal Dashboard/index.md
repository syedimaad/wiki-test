**Three Main Components**

1.  Athena Data Fetching

2.  DynamoDB/MongoDB Data Storing

3.  streamlit app

**Architecture**

**[File Directory Structure]{.underline}**

**Gitlab**:
[[https://gitlab.dailyhunt.in/josh-ai-labs/reco-dashboard/-/tree/master/]{.underline}](https://gitlab.dailyhunt.in/josh-ai-labs/reco-dashboard/-/tree/master/)

**Server:**
[http://10.10.33.157:1234/data/saikrishna/dashboards-master/all_projects/Daily_Metrics/](http://10.10.33.157:1234/edit/saikrishna/dashboards-master/all_projects/Daily_Metrics/fetch_athena_data/utils/utils.py)

**Structure Explanation**

- fetch_athena_data/athena_queries.py contains all query\`s

- fetch_athena_data/athena_helper.py will perform asynchronous calls to
  aws athena

- fetch_athena_data**/**Extract_athena_data.py will perform step 1 and
  step 2 (i.e fetching data from athena and storing it in documentDB)

- fetch_athena_data**/**Multidays_fetch_athena_data.py will perform the
  same above operation only but for multiple days

- utils/mongodb_manager.py is used for fetching data from documentDB

- App.py and app_helper.py are streamlit applications

streamlit link for internal dashboard : <http://10.10.33.157:8502/>
