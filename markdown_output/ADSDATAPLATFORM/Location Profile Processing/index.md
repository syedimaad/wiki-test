1.  VM where location processors run -
    dh-gcp-ads-dataproc-ek-n2.dailyhunt.in

2.  Path on the VM - /mnt/**vol2**/dh-ads-data/locationprofileprocessing

3.  Git Repo -
    <https://gitlab.dailyhunt.in/nh-ads-platform/locationprofileprocessing>

4.  Restart script -

    1.  \* \* \* \* \*
        /mnt/vol2/dh-ads-data/locationprofileprocessing/scripts/startAdsLocationProfileProcessor.sh
        \"/mnt/vol1/python3.8/bin/python
        adsProfileProcessing/requestsProcessor.py DH\" 97 \"bin/run.sh
        adsProfileProcessing/requestsProcessor.py DH\" \>\>
        /tmp/cronlogDH 2\>&1 \* \* \* \* \*
        /mnt/vol2/dh-ads-data/locationprofileprocessing/scripts/startAdsLocationProfileProcessor.sh
        \"/mnt/vol1/python3.8/bin/python
        adsProfileProcessing/requestsProcessor.py JOSH\" 13 \"bin/run.sh
        adsProfileProcessing/requestsProcessor.py JOSH\" \>\>
        /tmp/cronlogJOSH 2\>&1 \* \* \* \* \*
        /mnt/vol2/dh-ads-data/locationprofileprocessing/scripts/s

5.  The process should process locations only from ingress zones
    (EVALUATE)

6.  Evaluate why affiliate partner id requests are not processed.

7.  #TODO - Batch writes to Redis and Analytics Kafka, Global object for
    redis and analytics kafka updates too, commit to Kafka after final
    write to Redis. (Redis should be the last update)

8.  #TODO - Add logs in case of failed status from location service.

9.  #TODO - If location.last_updated key is not present in Redis (in
    case new source has lower precedence than redis source), then update
    with new source and add last_updated.

10. #TODO - Convert list of gps_location_cities to set in **init**
    function in LocationServiceHelper.

11. Grafana monitoring -
    <http://saluber.dailyhunt.in/d/kafkastats/kafka-stats?viewPanel=12&orgId=22&from=now-5m&to=now>

    1.  Consumer group DH - `kafka-mongo-req-consumer`

    2.  Josh - `kafka-mongo-req-consumer`-josh

    3.  PV - `kafka-mongo-req-consumer`-pv

12. Usual scenarios when lag increases:

    1.  Increase in traffic (increase batch size or decrease trigger
        interval)

    2.  Incorrect data in Kafka topic (records are pushed to faulty
        kafka topic, check there)

    3.  Slowness in location service

    4.  Mongo service is down

13. #TODO- Move lag checker script to different VM.

14. Confluent path - /mnt/vol1/dh-ads/confluent-7.3.2 - to run console
    consumers to verify data being sent to analytics kafka.

15. Crons for null city ids and tier wise reports:

    1.  00 00 01 \* \* bin/run.sh scripts/tierWiseDistributionMailer.py
        30 \>\> /tmp/tierWiseMailer 2\>&1 50 11 \* \* \* bin/run.sh
        scripts/nullCityIDs.py \>\> /tmp/nullCityIDs 2\>&1

16. Pip freeze

    1.  anyio==3.6.2 appdirs==1.4.4 argon2-cffi==21.3.0
        argon2-cffi-bindings==21.2.0 arrow==1.2.3 asttokens==2.2.1
        async-timeout==4.0.2 attrs==22.2.0 awscli==1.11.106
        backcall==0.2.0 backoff==1.6.0 backports-abc==0.5
        backports.shutil-get-terminal-size==1.0.0
        backports.ssl-match-hostname==3.5.0.1 beautifulsoup4==4.3.2
        bitarray==2.7.3 bleach==3.0.2 botocore==1.5.69 bottle==0.12.8
        cachetools==2.1.0 certifi==2018.10.15 cffi==1.15.1
        chardet==3.0.4 charset-normalizer==3.1.0 colorama==0.3.7
        comm==0.1.2 configparser==3.5.0 cramjam==2.6.2 crc32c==1.7
        cycler==0.9.0 cypari==2.4.1 debugpy==1.6.6 decorator==4.3.0
        defusedxml==0.5.0 Django==1.5.5 django-admin-tools==0.5.2
        django-allauth==0.19.1 django-debug-toolbar==1.3.0
        django-multidb-router==0.6 django-tables2==0.16.0
        dnspython==2.3.0 docutils==0.13.1 elasticsearch==5.3.0
        entrypoints==0.2.3 enum34==1.1.6 executing==1.2.0
        fastjsonschema==2.16.3 fastparquet==2023.4.0 Flask==0.10.1
        fqdn==1.5.1 fsspec==2023.5.0 funcsigs==1.0.2 future==0.16.0
        futures==3.1.1 FXrays==1.3.3 google-api-core==2.11.0
        google-api-python-client==1.7.4 google-auth==2.19.0
        google-auth-httplib2==0.0.3 google-auth-oauthlib==0.2.0
        google-cloud-core==2.3.2 google-cloud-storage==2.9.0
        google-crc32c==1.5.0 google-resumable-media==2.5.0
        googleapis-common-protos==1.59.0 httplib2==0.11.3 idna==2.7
        importlib-metadata==6.0.0 importlib-resources==5.12.0
        impyla==0.18.0 iniparse==0.4 ipaddress==1.0.22 ipykernel==5.5.6
        ipython==6.5.0 ipython-genutils==0.2.0 ipywidgets==7.4.2
        isoduration==20.11.0 itsdangerous==0.24 jedi==0.18.2
        Jinja2==3.1.2 jmespath==0.9.3 jsonpointer==2.3
        jsonschema==4.17.3 jupyter==1.0.0 jupyter-client==5.2.3
        jupyter-console==5.2.0 jupyter-core==4.4.0 jupyter-events==0.6.3
        jupyter_server==2.4.0 jupyter_server_terminals==0.4.4
        jupyterlab-pygments==0.2.2 kafka-python==2.0.2
        knot-floer-homology==1.2 MarkupSafe==2.1.2 matplotlib==1.5.2
        matplotlib-inline==0.1.6 memory-profiler==0.47 mistune==0.8.4
        mock==2.0.0 mongo==0.2.0 mongoengine==0.9.0 nats-py==2.3.1
        nats-python==0.8.0 nbclassic==0.5.3 nbclient==0.7.2
        nbconvert==5.4.0 nbformat==4.4.0 nest-asyncio==1.5.6
        networkx==1.11 nltk==3.0.2 notebook==5.7.0 notebook_shim==0.2.2
        numpy==1.24.2 oauth2client==4.1.3 oauthlib==2.1.0
        packaging==20.9 pandas==1.5.3 pandocfilters==1.4.2 parso==0.8.3
        path.py==8.1.2 pathlib2==2.3.2 patsy==0.4.1 pbr==4.0.3
        pexpect==4.6.0 pickleshare==0.7.4 Pillow==9.4.0
        pkgutil_resolve_name==1.3.10 platformdirs==3.1.0 plink==2.2
        ply==3.11 prometheus-client==0.4.2 prompt-toolkit==1.0.15
        protobuf==4.23.2 psutil==5.9.4 ptyprocess==0.6.0
        pure-eval==0.2.2 pure-sasl==0.6.2 pyasn1==0.4.8
        pyasn1-modules==0.2.2 pycparser==2.20 pycrypto==2.6.1
        PyDrive==1.3.1 Pygments==2.2.0 pymongo==3.8.0 pyparsing==2.1.0
        pypng==0.0.18 pyrsistent==0.19.3 python-dateutil==2.8.2
        python-json-logger==2.0.7 python-Levenshtein==0.12.0
        python-lzf==0.2.4 python-openid==2.2.5 python3-openid==3.2.0
        pytz==2022.7.1 pyudev==0.15 PyYAML==3.12 pyzmq==17.1.2
        qtconsole==4.4.2 QtPy==2.3.0 rdbtools==0.1.14 redis==2.10.5
        redis-py-cluster==1.2.0 repoze.lru==0.7 requests==2.19.1
        requests-oauthlib==1.0.0 rfc3339-validator==0.1.4
        rfc3986-validator==0.1.1 rsa==3.4.2 s3transfer==0.1.10
        scandir==1.7 scipy==1.10.1 Send2Trash==1.5.0
        simplegeneric==0.8.1 simplejson==3.10.0 singledispatch==3.4.0.3
        six==1.16.0 snap==0.5 snappy==2.6 snappy-manifolds==1.0
        sniffio==1.3.0 spherogram==1.8 sqlparse==0.1.15
        stack-data==0.6.2 statsd==3.3.0 terminado==0.8.1 testpath==0.4.2
        tflearn==0.3.2 thrift==0.16.0 thrift-sasl==0.4.3 tinycss2==1.2.1
        tornado==5.1.1 tqdm==4.65.0 traitlets==4.3.2 ujson==5.7.0
        uri-template==1.2.0 uritemplate==3.0.0 urllib3==1.23
        virtualenv==16.0.0 wcwidth==0.1.7 webcolors==1.12
        webencodings==0.5.1 websocket-client==1.5.1 Werkzeug==0.10.4
        widgetsnbextension==3.4.2 xlrd==0.9.3 zipp==3.15.0
