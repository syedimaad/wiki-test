### Jupyter

#Command to list notebooks with tokens jupyter-notebook list #Each node
has two jupyter notebooks running on screen. #screen names - jupyter and
jupyter2  #Run below commands to start jupyter notebook server on above
screen respectively    screen -ls screen -S jupyter  screen -S jupyter2
\# To set or reset Password jupyter notebook password jupyter-notebook
\--ip=0.0.0.0 \--no-browser \--port=8888 jupyter-notebook \--ip=0.0.0.0
\--no-browser \--port=8889

### How to get started with Jupyter Notebook

\# Create your virtual environment in your \<user\> directory python3 -m
venv .unified_model \# activate the virtual environment source
.unified_model/bin/activate \# install ipykernel pip install ipykernel
python3 -m ipykernel install \--user \--name=.unified_model

  ------------------------------------------------------------------------------------------- -------------
  [perf.ads.jupyter1-n3.dailyhunt.in/groot](http://perf.ads.jupyter1-n3.dailyhunt.in/groot)   ads-perf
  [perf.ads.jupyter2-n3.dailyhunt.in/groot](http://perf.ads.jupyter2-n3.dailyhunt.in/groot)   ads-perf
  [perf.ads.jupyter1-n7.dailyhunt.in/groot](http://perf.ads.jupyter1-n7.dailyhunt.in/groot)   Not running
  [perf.ads.jupyter2-n7.dailyhunt.in/groot](http://perf.ads.jupyter2-n7.dailyhunt.in/groot)   Not running
  [perf.ads.jupyter1-n8.dailyhunt.in/groot](http://perf.ads.jupyter1-n8.dailyhunt.in/groot)   Not running
  [perf.ads.jupyter2-n8.dailyhunt.in/groot](http://perf.ads.jupyter2-n8.dailyhunt.in/groot)   Not running
  [perf.ads.jupyter1-n9.dailyhunt.in/groot](http://perf.ads.jupyter1-n9.dailyhunt.in/groot)   ads-perf
  [perf.ads.jupyter2-n9.dailyhunt.in/groot](http://perf.ads.jupyter2-n9.dailyhunt.in/groot)   ads-perf
  ------------------------------------------------------------------------------------------- -------------

\

### YARN

  -------------- ------------------------------ ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  10.50.16.45    Yarn master GUI                [[Yarn.master-n2.dailyhunt.in]{.underline}](http://yarn.master-n2.dailyhunt.in/),[[yarn.master-n1.dailyhunt.in]{.underline}](http://yarn.master-n2.dailyhunt.in/), [[http://dh-gcp-ads-learning-sparkhdfs-n1.dailyhunt.in:8088/ui2/#/yarn-apps/apps]{.underline}](http://dh-gcp-ads-learning-sparkhdfs-n1.dailyhunt.in:8088/ui2/#/yarn-apps/apps)
  10.50.16.46                                   
                                                
  10.50.16.46    Mapreduce History Server GUI   [[http://mapreduce.history.dailyhunt.in/]{.underline}](http://mapreduce.history.dailyhunt.in/)
                                                
  10.50.16.45    Spark History GUI              [[spark.history.dailyhunt.in]{.underline}](http://spark.history.dailyhunt.in/)
  10.50.19.201   Perf Edge VM                   <http://10.50.19.201:8005/>
  10.50.16.45    Grafana for HDP                [[grafana.hadoop.dailyhunt.in]{.underline}](http://grafana.hadoop.dailyhunt.in/)
  10.50.16.47    Performance Dashboards         [[5101 : ads-perf-health-check.dailyhunt.in]{.underline}](http://ads-perf-health-check.dailyhunt.in/), 5102: [[ads-experimentation-platform.dailyhunt.in]{.underline}](http://ads-experimentation-platform.dailyhunt.in/), 5103: [[ads-perf-expt.dailyhunt.in]{.underline}](http://ads-perf-expt.dailyhunt.in/) (Note: 5103 is for testing).
  -------------- ------------------------------ ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Airflow 

[[http://dh-gcp-ads-learning-sparkhdfs-n3.dailyhunt.in:8080/admin/]{.underline}](http://dh-gcp-ads-learning-sparkhdfs-n3.dailyhunt.in:8080/admin/)

[[http://dh-gcp-ads-learning-sparkhdfs-n9.dailyhunt.in:8080/admin/]{.underline}](http://dh-gcp-ads-learning-sparkhdfs-n9.dailyhunt.in:8080/admin/)

[[http://dh-gcp-ads-learning-n1.dailyhunt.in:8080/admin/]{.underline}](http://dh-gcp-ads-learning-n1.dailyhunt.in:8080/admin/)

#### To restart airflow 

pkill -f airflow #Post this auto-restarts \#### #Below command does not
kill older process supervisorctl restart airflow-web  supervisorctl
restart airflow-scheduler

  
