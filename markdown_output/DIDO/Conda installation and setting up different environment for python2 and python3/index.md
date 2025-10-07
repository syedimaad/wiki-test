1.Download  Anaconda3-5.2.0

\

cd /tmp curl -O
https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh

2.Verify the Data Integrity of the Installer

sha256sum Anaconda3-5.2.0-Linux-x86_64.sh

3.Run the script using bash

bash Anaconda3-5.2.0-Linux-x86_64.sh

4.Verify the PATH variable

\$ echo \$PATH
/mnt/vol1/dh-ads/bin:/mnt/vol1/dh-ads/.local/bin:/mnt/vol1/dh-ads/anaconda3/bin:/mnt/vol1/dh-ads/anaconda2/bin:/mnt/vol1/jdk1.7.0_80/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/usr/java/jdk1.7.0_80/bin

5.Create,activate and deactivate env for different python version

\

conda create -n Python27 python=2.7 source activate Python27 source
deactivate Python27 conda create -n Python35 python=3.5 source activate
Python35 source deactivate Python35

\
\
6.check and verify the env added

\

\$ conda env list \# conda environments: \#
/mnt/vol1/dh-ads/anaconda2/envs/Python27
/mnt/vol1/dh-ads/anaconda2/envs/Python35 base /mnt/vol1/dh-ads/anaconda3
Python27 /mnt/vol1/dh-ads/anaconda3/envs/Python27 Python35
/mnt/vol1/dh-ads/anaconda3/envs/Python35

\

7.conda Install and list for different env

\

\$ which conda /mnt/vol1/dh-ads/anaconda3/bin/conda \$ conda list
\|egrep \'pytorch\|tensorflow\|xgboost\|pyspark\' pyspark 2.3.2 \<pip\>
pytorch 0.4.1 py36ha74772b_0 tensorflow 1.10.1 \<pip\> xgboost 0.80
\<pip\> \$conda install -n Python27 tensorflow \$conda install -n
Python27 pytorch \$conda list -n Python27 \|egrep
\'pytorch\|tensorflow\' pytorch 0.4.1 py27ha74772b_0 tensorflow 1.10.0
mkl_py27h857755f_0 tensorflow-base 1.10.0 mkl_py27h3c3e929_0

\

**-Sanal K**
