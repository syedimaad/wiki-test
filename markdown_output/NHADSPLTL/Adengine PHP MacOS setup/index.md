Execute below commands -

bashbrew install homebrewbashbrew tap shivammathur/phpbashbrew install
shivammathur/php/php@7.2-debugbashbrew link \--overwrite \--force
shivammathur/php/php@7.2-debugbashecho \'export
PATH=\"/opt/homebrew/opt/php@7.2-debug/bin:\$PATH\"\' \>\> \~/.zshrc
echo \'export PATH=\"/opt/homebrew/opt/php@7.2/sbin:\$PATH\"\' \>\>
\~/.zshrcbashphp -vbashbrew install nginx

8)clone adengine repo from here
<https://gitlab.dailyhunt.in/nh-ads-platform/adEngine> add env file in
adengine repo.

9)add  `listen=127.0.0.1:9001`  at the end of
/opt/homebrew/etc/php/7.2/php-fpm.conf

10)you need the following php extensions \[grpc,protobuff,redis,xdebug\]

pecl install grpc pecl install protobuf-3.19.4 pecl install redis pecl
install xdebug

11)install protoc and grpc php plugin.

git clone https://github.com/grpc/grpc cd grpc git submodule update
\--init mkdir -p cmake/build cd cmake/build cmake ../.. make protoc
grpc_php_plugin //export grpc_php_plugin path as \$GRPC_PLUGIN_PATH this
will be used by script in adengine,to compile proto files.

12)compile proto files using this script

/Users/harshavardhana.reddy/Projects/nh-ads-platform/adEngine/src/Lib/Entities/Proto/generateProtoFiles.sh

13)Launch debugger in vscode with port 9003

append these lines at the end of php.ini \[xdebug\]
xdebug.start_with_request=yes xdebug.mode=debug xdebug.client_host =
127.0.0.1 xdebug.client_port = 9003 xdebug.show_exception_trace = On
xdebug.remote_handler = dbgp

14)Install brotli extension from here
[https://github.com/kjdev/php-ext-brotli](https://github.com/kjdev/php-ext-brotli){card-appearance="inline"}\
and add it to to php.ini.\

ngnixconf:

#user nobody; worker_processes 1; #error_log logs/error.log; #error_log
logs/error.log notice; #error_log logs/error.log info; #pid
logs/nginx.pid; events { worker_connections 1024; } http { include
mime.types; default_type application/octet-stream; #log_format main
\'\$remote_addr - \$remote_user \[\$time_local\] \"\$request\" \' \#
\'\$status \$body_bytes_sent \"\$http_referer\" \' \#
\'\"\$http_user_agent\" \"\$http_x_forwarded_for\"\'; #access_log
logs/access.log main; sendfile on; #tcp_nopush on; #keepalive_timeout 0;
keepalive_timeout 65; #gzip on; server { listen 80 default_server;
server_name localhost; root
/Users/harshavardhan.reddy/Projects/nh-ads-platform/adEngine/public;
index index.php index.html index.htm; #charset koi8-r; #access_log
logs/host.access.log main; #error_page 404 /404.html; \# redirect server
error pages to the static page /50x.html \# error_page 500 502 503 504
/50x.html; location = /50x.html { root html; } location \~\*
.(\\.php\|cacheRefresh\|impression\|vastevent\|beaconEvents\|click\|fallback\|tracker\|fetchCampaignData\|aggressiveCacherMeta\|aggressiveCacher\|aggressiveCacheQueueConsumer\|aggressiveCacheInitiator\|getvast\|getvmap\|ApcCacher\|webHandshake\|instlpostback\|ads\|getBids\|prebidEvents\|appeventpostback\|token\|dhDdc\|decodeAup\|redirect)\$
{ try_files \$uri /index.php =404; fastcgi_split_path_info
\^(.+\\.php)(/.+)\$; fastcgi_pass 127.0.0.1:9001; fastcgi_index
index.php; fastcgi_param SCRIPT_FILENAME
\$document_root\$fastcgi_script_name; fastcgi_param SCRIPT_NAME
\$fastcgi_script_name; include fastcgi_params; fastcgi_buffers 16 16k;
fastcgi_buffer_size 32k; #rewrite /openx/ads/index.php(.\*) /index/\$1
last; if (!-e \$request_filename){ rewrite \^(.\*)\$ /index.php break; }
} location \~\* \^.+.(ico\|xml\|js\|css\|jpg\|png\|jpeg\|gif)\$ {
access_log off; expires 30d; root
/Users/harshavardhan.reddy/Projects/nh-ads-platform/adEngine/public; }
\# proxy the PHP scripts to Apache listening on 127.0.0.1:80 \#
#location \~ \\.php\$ { \# proxy_pass http://127.0.0.1; #} \# pass the
PHP scripts to FastCGI server listening on 127.0.0.1:9000 \# #location
\~ \\.php\$ { \# root html; \# fastcgi_pass 127.0.0.1:9000; \#
fastcgi_index index.php; \# fastcgi_param SCRIPT_FILENAME
/scripts\$fastcgi_script_name; \# include fastcgi_params; #} \# deny
access to .htaccess files, if Apache\'s document root \# concurs with
nginx\'s one \# #location \~ /\\.ht { \# deny all; #} } \# another
virtual host using mix of IP-, name-, and port-based configuration \#
#server { \# listen 8000; \# listen somename:8080; \# server_name
somename alias another.alias; \# location / { \# root html; \# index
index.html index.htm; \# } #} \# HTTPS server \# #server { \# listen 443
ssl; \# server_name localhost; \# ssl_certificate cert.pem; \#
ssl_certificate_key cert.key; \# ssl_session_cache shared:SSL:1m; \#
ssl_session_timeout 5m; \# ssl_ciphers HIGH:!aNULL:!MD5; \#
ssl_prefer_server_ciphers on; \# location / { \# root html; \# index
index.html index.htm; \# } #} include servers/\*; }

.env.php:

\<?php /\* return \[ \'LOG_LEVEL\' =\> LOG_DEBUG, \'ENV\' =\> \'PROD\',
\'DAEDALUS_DB_HOST\' =\> \'10.52.136.21\', \'DAEDALUS_DB_PORT\' =\>
\'3306\', \'DAEDALUS_DB_USER\' =\> \'adserve\', \'DAEDALUS_DB_PASSWORD\'
=\> \'Etern0@!23\', \'DAEDALUS_DB_NAME\' =\> \'daedalus\',
\'DAEDALUS_MASTER_DB_HOST\' =\> \'10.52.136.21\',
\'DAEDALUS_MASTER_DB_PORT\' =\> \'3306\', \'DAEDALUS_MASTER_DB_USER\'
=\> \'root\', \'DAEDALUS_MASTER_DB_PASSWORD\' =\> \'Etern0@!23\',
\'DAEDALUS_MASTER_DB_NAME\' =\> \'daedalus\', \'OADS_DB_HOST\' =\>
\'10.52.136.21\', \'OADS_DB_PORT\' =\> \'3306\', \'OADS_DB_USER\' =\>
\'root\', \'OADS_DB_PASSWORD\' =\> \'Etern0@!23\', \'OADS_DB_NAME\' =\>
\'oads\', \'OADS_MASTER_DB_HOST\' =\> \'10.52.136.21\',
\'OADS_MASTER_DB_PORT\' =\> \'3306\', \'OADS_MASTER_DB_USER\' =\>
\'root\', \'OADS_MASTER_DB_PASSWORD\' =\> \'Etern0@!23\',
\'OADS_MASTER_DB_NAME\' =\> \'oads\', \'MASTER_DB_HOST\' =\>
\'10.52.136.21\', \'MASTER_DB_PORT\' =\> \'3306\', \'MASTER_DB_USER\'
=\> \'root\', \'MASTER_DB_PASSWORD\' =\> \'Etern0@!23\',
\'MASTER_DB_NAME\' =\> \'oads\', \'DOMAIN_NAME\' =\>
!empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'money.dailyhunt.in\',
\'TRACKER_DOMAIN_NAME\' =\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'money.dailyhunt.in\',
\'IMAGE_DOMAIN_NAME\' =\> \'acdn.newshuntads.com\',
\'BEACON_DOMAIN_NAME\' =\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'money.dailyhunt.in\',
\'CLICK_DOMAIN_NAME\' =\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'money.dailyhunt.in\',
\'COOKIE_DOMAIN_NAME\' =\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'money.dailyhunt.in\',
\'PARENT_COOKIE_DOMAIN_NAME\' =\> \'.dailyhunt.in\',
\'FORCE_ENV_COOKIE_DOMAIN\' =\> 1, \'CACHE_TIMEOUT\' =\> 36000,
\'REDIS_DATA_CACHE_TIMEOUT\' =\> 600, \'EMPTY_BANNER_ID\' =\> \'53495\',
\'EMPTY_FALLBACK_BANNER_ID\' =\> \'53496\', \'EMPTY_CAMPAIGN_ID\' =\>
\'-2\', \'REJECTED_ZONE_EMPTY_BANNER_ID\' =\> \'53495\',
\'QUEUE_REDIS_CLUSTER\' =\>
\'tcp://192.168.24.36:7001?slots=3372&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7001?slots=4014&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7002?slots=5808&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7003?slots=11174&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7004?slots=15553&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7001?slots=3372&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7001?slots=4014&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7002?slots=5808&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7003?slots=11174&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7004?slots=15553&persistent=1&timeout=0.001&read_write_timeout=0.001\',
\'PERSISTENT_REDIS_CLUSTER\' =\>
\'cache-n10.internal.ads.dailyhunt.in:8003,cache-n12.internal.ads.dailyhunt.in:8004,cache-n7.internal.ads.dailyhunt.in:8002,cache-n1.internal.ads.dailyhunt.in:8001,cache-n7.internal.ads.dailyhunt.in:8001,cache-n9.internal.ads.dailyhunt.in:8004,cache-n4.internal.ads.dailyhunt.in:8002,cache-n8.internal.ads.dailyhunt.in:8002,cache-n4.internal.ads.dailyhunt.in:8001,cache-n15.internal.ads.dailyhunt.in:8003,cache-n6.internal.ads.dailyhunt.in:8001,cache-n2.internal.ads.dailyhunt.in:8002,cache-n16.internal.ads.dailyhunt.in:8004,cache-n3.internal.ads.dailyhunt.in:8002,cache-n1.internal.ads.dailyhunt.in:8002,cache-n2.internal.ads.dailyhunt.in:8001,cache-n11.internal.ads.dailyhunt.in:8004,cache-n14.internal.ads.dailyhunt.in:8003,cache-n15.internal.ads.dailyhunt.in:8004,cache-n16.internal.ads.dailyhunt.in:8003,cache-n11.internal.ads.dailyhunt.in:8003,cache-n10.internal.ads.dailyhunt.in:8004,cache-n3.internal.ads.dailyhunt.in:8001,cache-n12.internal.ads.dailyhunt.in:8003,cache-n8.internal.ads.dailyhunt.in:8001,cache-n6.internal.ads.dailyhunt.in:8002,cache-n9.internal.ads.dailyhunt.in:8003,cache-n14.internal.ads.dailyhunt.in:8004,cache-n9.internal.ads.dailyhunt.in:8002,cache-n1.internal.ads.dailyhunt.in:8004,cache-n12.internal.ads.dailyhunt.in:8002,cache-n15.internal.ads.dailyhunt.in:8001,cache-n7.internal.ads.dailyhunt.in:8003,cache-n8.internal.ads.dailyhunt.in:8004,cache-n10.internal.ads.dailyhunt.in:8001,cache-n2.internal.ads.dailyhunt.in:8003,cache-n11.internal.ads.dailyhunt.in:8002,cache-n16.internal.ads.dailyhunt.in:8002,cache-n11.internal.ads.dailyhunt.in:8001,cache-n9.internal.ads.dailyhunt.in:8001,cache-n6.internal.ads.dailyhunt.in:8004,cache-n1.internal.ads.dailyhunt.in:8003,cache-n7.internal.ads.dailyhunt.in:8004,cache-n12.internal.ads.dailyhunt.in:8001,cache-n16.internal.ads.dailyhunt.in:8001,cache-n8.internal.ads.dailyhunt.in:8003,cache-n4.internal.ads.dailyhunt.in:8004,cache-n15.internal.ads.dailyhunt.in:8002,cache-n3.internal.ads.dailyhunt.in:8003,cache-n10.internal.ads.dailyhunt.in:8002,cache-n14.internal.ads.dailyhunt.in:8001,cache-n2.internal.ads.dailyhunt.in:8004,cache-n4.internal.ads.dailyhunt.in:8003,cache-n14.internal.ads.dailyhunt.in:8002,cache-n3.internal.ads.dailyhunt.in:8004,cache-n6.internal.ads.dailyhunt.in:8003\',
\'SUPPLEMENT_LOG_ENABLED\' =\> false, \'CONTEXTUAL_ADS_KAFKA_HOST\' =\>
\'dh-kafka-n1.rtp.dailyhunt.in:9092,dh-kafka-n2.rtp.dailyhunt.in:9092,dh-kafka-n3.rtp.dailyhunt.in:9092,dh-beacon-n1.rtp.dailyhunt.in:9092,dh-beacon-n2.rtp.dailyhunt.in:9092,dh-beacon-n3.rtp.dailyhunt.in:9092,dh-beacon-n4.rtp.dailyhunt.in:9092,dh-beacon-n5.rtp.dailyhunt.in:9092\',
\'CONTEXTUAL_ADS_KAFKA_TOPIC\' =\> \'ad_contextual_item_assoc\',
\'CONTEXTUAL_ADS_DATA_FILE\' =\> dirname(\_\_FILE\_\_) .
\'/logs/ContextualAdsData.json\', \'ELASTIC_SEARCH_HOSTS\' =\>
\[\'ie-n1.internal.ads.dailyhunt.in\',
\'ie-n2.internal.ads.dailyhunt.in\',
\'ie-n3.internal.ads.dailyhunt.in\'\], \'ELASTIC_SEARCH_PORT\' =\> 9200,
\'ELASTIC_SEARCH_USER\' =\> \'newsAdmin\', \'ELASTIC_SEARCH_PASS\' =\>
\'news@dmin4u\', \'CORS_ENABLED_DOMAINS\' =\>
\[\'https://m.dailyhunt.in\', \'https://web.dailyhunt.in\',
\'https://samsung.dailyhunt.in\', \'https://xiaomi.dailyhunt.in\',
\'https://webqa.dailyhunt.in\', \'http://api-news.dailyhunt.in\',
\'https://api-news.dailyhunt.in\', \'https://pre.dailyhunt.in\',
\'https://pwa.dailyhunt.in\', \'https://nearme.dailyhunt.in\',
\'https://vivo.dailyhunt.in\', \'https://infinix.dailyhunt.in\',
\'https://tecno.dailyhunt.in\', \'https://itel.dailyhunt.in\',
\'https://indus.dailyhunt.in\', \'http://mozilla.dailythunt.in\',
\'https://mozilla.dailythunt.in\'\], \'KAFKA_PRODUCER_URL\' =\>
\'http://dh-ads-kafka-nrt.dailyhunt.in/topics/\',
\'AGGRESSIVE_CACHER_KAFKA_BROKERS\' =\>
\"kafka-n1.internal.ads.dailyhunt.in:9092\",
\"kafka-n2.internal.ads.dailyhunt.in:9092\",
\"kafka-n3.internal.ads.dailyhunt.in:9092\",
\"kafka-n4.internal.ads.dailyhunt.in:9092\",
\"kafka-n5.internal.ads.dailyhunt.in:9092\",
\"kafka-n6.internal.ads.dailyhunt.in:9092\",
\"kafka-n7.internal.ads.dailyhunt.in:9092\",
\"kafka-n8.internal.ads.dailyhunt.in:9092\",
\'AGGRESSIVE_CACHER_KAFKA_PRODUCER_URL\' =\>
\'http://dh-ads-kafka-nrt.dailyhunt.in/topics/\',
\'AGGRESSIVE_CACHER_KAFKA_SOCKET_TIMEOUT\' =\> 5000, // this is in
milliseconds \'AGGRESSIVE_CACHER_KAFKA_READ_TIMEOUT\' =\> 5000, // this
is in milliseconds \'AGGRESSIVE_CACHER_KAFKA_GROUP_ID\' =\> \'ag\_\' .
gethostname(), \'AGGRESSIVE_CACHER_KAFKA_TOPIC\' =\>
\'AggressiveCacheTopic\', \'AGGRESSIVE_CACHER_KAFKA_SLEEP_TIME\' =\> 5,
//\'MASTER_DOMAIN_NAME_FOR_API\' =\> \'master.newshuntads.com\'
\'MASTER_DOMAIN_NAME_FOR_API\' =\> \'adsmaster.dailyhunt.in\',
\'RANKING_SERVICE_CALL_TIMEOUT_IN_MicS\' =\> 20000,
\'RANKING_SERVICE_HOSTNAME_PORT\' =\>
\'dh-ranking-service.dailyhunt.in:443\',
\'RANKING_SERVICE_SSL_CERT_PATH\' =\>
\'/etc/pki/tls/certs/dailyhunt_public.cer\', \]; \*/ #LOG_LEVEL values
\[ INFO / DEBUG / CRITICAL \] return \[ \'LOG_LEVEL\' =\> LOG_DEBUG,
\'ENV\' =\> \'prod\', \'DAEDALUS_DB_HOST\' =\> \'10.52.24.11\',
\'DAEDALUS_DB_PORT\' =\> \'3306\', \'DAEDALUS_DB_USER\' =\> \'root\',
\'DAEDALUS_DB_PASSWORD\' =\> \'ROot54348\', \'DAEDALUS_DB_NAME\' =\>
\'daedalus\', \'DAEDALUS_MASTER_DB_HOST\' =\> \'10.52.24.11\',
\'DAEDALUS_MASTER_DB_PORT\' =\> \'3306\', \'DAEDALUS_MASTER_DB_USER\'
=\> \'root\', \'DAEDALUS_MASTER_DB_PASSWORD\' =\> \'ROot54348\',
\'DAEDALUS_MASTER_DB_NAME\' =\> \'daedalus\', \'OADS_DB_HOST\' =\>
\'10.52.24.11\', \'OADS_DB_PORT\' =\> \'3306\', \'OADS_DB_USER\' =\>
\'root\', \'OADS_DB_PASSWORD\' =\> \'ROot54348\', \'OADS_DB_NAME\' =\>
\'oads\', \'OADS_MASTER_DB_HOST\' =\> \'10.52.24.11\',
\'OADS_MASTER_DB_PORT\' =\> \'3306\', \'OADS_MASTER_DB_USER\' =\>
\'root\', \'OADS_MASTER_DB_PASSWORD\' =\> \'ROot54348\',
\'OADS_MASTER_DB_NAME\' =\> \'oads\', \'MASTER_DB_HOST\' =\>
\'10.52.24.11\', \'MASTER_DB_PORT\' =\> \'3306\', \'MASTER_DB_USER\' =\>
\'root\', \'MASTER_DB_PASSWORD\' =\> \'ROot54348\', \'MASTER_DB_NAME\'
=\> \'oads\', \'DOMAIN_NAME\' =\>
!empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'localhost\',
\'TRACKER_DOMAIN_NAME\' =\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'localhost\', \'IMAGE_DOMAIN_NAME\'
=\> \'localhost\', \'BEACON_DOMAIN_NAME\' =\>
!empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'localhost\', \'CLICK_DOMAIN_NAME\'
=\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'localhost\', \'COOKIE_DOMAIN_NAME\'
=\> !empty(\$\_SERVER\[\'HTTP_TRUE_HOST\'\]) ?
\$\_SERVER\[\'HTTP_TRUE_HOST\'\] : \'localhost\',
\'PARENT_COOKIE_DOMAIN_NAME\' =\> \'localhost\',
\'FORCE_ENV_COOKIE_DOMAIN\' =\> 1, \'CACHE_TIMEOUT\' =\> 1,
\'REDIS_DATA_CACHE_TIMEOUT\' =\> 1, \'EMPTY_BANNER_ID\' =\> \'80580\',
\'EMPTY_FALLBACK_BANNER_ID\' =\> \'53495\', \'NEW_USER_EMPTY_BANNER_ID\'
=\> \'80580\', \'EMPTY_CAMPAIGN_ID\' =\> \'-2\', \'QUEUE_REDIS_CLUSTER\'
=\>
\'tcp://192.168.24.36:7001?slots=3372&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7001?slots=4014&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7002?slots=5808&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7003?slots=11174&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7004?slots=15553&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7001?slots=3372&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7001?slots=4014&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7002?slots=5808&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.37:7003?slots=11174&persistent=1&timeout=0.001&read_write_timeout=0.001,tcp://192.168.24.36:7004?slots=15553&persistent=1&timeout=0.001&read_write_timeout=0.001\',
\'PERSISTENT_REDIS_CLUSTER\' =\>
\'10.52.0.24:7000,10.52.0.25:7000,10.52.0.26:7000\',
\'SUPPLEMENT_LOG_ENABLED\' =\> false, \'CONTEXTUAL_ADS_KAFKA_HOST\' =\>
\'dh-kafka-n1.rtp.dailyhunt.in:9092,dh-kafka-n2.rtp.dailyhunt.in:9092,dh-kafka-n3.rtp.dailyhunt.in:9092,dh-beacon-n1.rtp.dailyhunt.in:9092,dh-beacon-n2.rtp.dailyhunt.in:9092,dh-beacon-n3.rtp.dailyhunt.in:9092,dh-beacon-n4.rtp.dailyhunt.in:9092,dh-beacon-n5.rtp.dailyhunt.in:9092\',
\'CONTEXTUAL_ADS_KAFKA_TOPIC\' =\> \'ad_contextual_item_assoc\',
\'CONTEXTUAL_ADS_DATA_FILE\' =\> dirname(\_\_FILE\_\_) .
\'/logs/ContextualAdsData.json\', \'ELASTIC_SEARCH_HOSTS\' =\>
\[\'ie-n1.internal.ads.dailyhunt.in\',
\'ie-n2.internal.ads.dailyhunt.in\',
\'ie-n3.internal.ads.dailyhunt.in\'\], \'ELASTIC_SEARCH_PORT\' =\> 9200,
\'ELASTIC_SEARCH_USER\' =\> \'newsAdmin\', \'ELASTIC_SEARCH_PASS\' =\>
\'news@dmin4u\', \'CORS_ENABLED_DOMAINS\' =\>
\[\'https://m.dailyhunt.in\', \'https://web.dailyhunt.in\',
\'https://samsung.dailyhunt.in\', \'https://xiaomi.dailyhunt.in\',
\'https://webqa.dailyhunt.in\', \'http://api-news.dailyhunt.in\',
\'https://api-news.dailyhunt.in\', \'https://pre.dailyhunt.in\',
\'https://pwa.dailyhunt.in\', \'https://nearme.dailyhunt.in\',
\'https://vivo.dailyhunt.in\', \'https://infinix.dailyhunt.in\',
\'https://tecno.dailyhunt.in\', \'https://itel.dailyhunt.in\',
\'https://indus.dailyhunt.in\', \'http://mozilla.dailythunt.in\',
\'https://mozilla.dailythunt.in\', \'http://api.adengine.com:3001\'\],
\'KAFKA_PRODUCER_URL\' =\>
\'http://dh-gcp-ads-kafka-stage-n1.dailyhunt.in:8082/topics/\',
\'AGGRESSIVE_CACHER_KAFKA_BROKERS\' =\>
\"dh-gcp-ads-kafka-stage-n1.dailyhunt.in:9092,dh-gcp-ads-kafka-stage-n2.dailyhunt.in:9092,dh-gcp-ads-kafka-stage-n3.dailyhunt.in:9092\",
\'AGGRESSIVE_CACHER_KAFKA_PRODUCER_URL\' =\>
\'http://dh-gcp-ads-kafka-stage-n1.dailyhunt.in:8082/topics/\',
\'AGGRESSIVE_CACHER_KAFKA_SOCKET_TIMEOUT\' =\> 5000, // this is in
milliseconds \'AGGRESSIVE_CACHER_KAFKA_READ_TIMEOUT\' =\> 5000, // this
is in milliseconds \'AGGRESSIVE_CACHER_KAFKA_GROUP_ID\' =\> \'ag\_\' .
gethostname(), \'AGGRESSIVE_CACHER_KAFKA_TOPIC\' =\>
\'AggressiveCacheTopic\', \'AGGRESSIVE_CACHER_KAFKA_SLEEP_TIME\' =\> 5,
//\'MASTER_DOMAIN_NAME_FOR_API\' =\> \'master.newshuntads.com\'
\'MASTER_DOMAIN_NAME_FOR_API\' =\> \'localhost\',
\'RANKING_SERVICE_CALL_TIMEOUT_IN_MicS\' =\> 200000000,
//\'RANKING_SERVICE_HOSTNAME_PORT\' =\>
\'dh-qa-ranking-service.dailyhunt.in:443\',
//\'RANKING_SERVICE_HOSTNAME_PORT\' =\>
\'dh-qa-ranking-service.dailyhunt.in:443\',
\'RANKING_SERVICE_HOSTNAME_PORT\' =\>
\'dh-stage-ranking-service.dailyhunt.in:443\',
\'RANKING_SERVICE_SSL_CERT_PATH\' =\>
\'/opt/homebrew/var/www/dailyhunt_public.cer\', \'S2SV2_DOMAIN_NAME\'
=\> \'10.52.15.204:8000\', \'LOCATION_SERVICE_DOMAIN_NAME\' =\>
\'locationservice.dailyhunt.in\', \'RANKING_SERVICE_USE_SSL\' =\> true,
\'SHOP_BAG_ICON_URL_LIGHT\' =\>
\'http://assets-money.dailyhunt.in/images/shop_bag_light.png\',
\'SHOP_BAG_ICON_URL_DARK\' =\>
\'http://assets-money.dailyhunt.in/images/shop_bag_dark.png\',
\'AD_SELECT_SERVICE_HOSTNAME_PORT\' =\> \'10.52.0.60:9092\',
\'AD_SELECT_SERVICE_USE_SSL\' =\> false,
\'AD_SELECT_SERVICE_CALL_TIMEOUT_IN_MicS\' =\> 1000000,
\'AD_SELECT_SERVICE_SSL_CERT_PATH\' =\>
\'/opt/homebrew/var/www/dailyhunt_public.cer\',
\'CATALOG_SERVICE_DOMAIN_NAME\' =\> \'http://stage-money.dailyhunt.in\',
\'CATALOG_SERVICE_ACCESS_TOKEN\' =\> \'6aNoAhL6N5SUp8z5rac11\',
\'GCP_PROJECT_ID\' =\> \'dh-gcp-ads-sandbox\',
\'BEACON_CLOUD_STORAGE_BUCKET\' =\>
\'dh-gcp-ads-adengine-error-beacons-bkt-stage\',
//\'BEACON_CLOUD_STORAGE_BUCKET\' =\>
\'dh-gcp-ads-adengine-error-beacons-qa\', \'CACHE_STORAGE_BUCKET\' =\>
\'sandbox_adengine_cache\' //\'CACHE_STORAGE_BUCKET\' =\>
\'stage_adengine_cache\' \];
