**1)Install AWS Cli on the respective machine.**

curl \"<https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip>\" -o
\"awscliv2.zip\"\
unzip awscliv2.zip\
sudo ./aws/install

**2)Copy logrotation scripts to the respective machine.**

cd /etc/logrotate.d/

cat logrotate_ffmpeg

/home/ubuntu/temp/ffmpeg_output\*.log {\
su ubuntu ubuntu\
dateext\
dateformat -%Y%m%d-%s\
copytruncate\
compress\
compresscmd /bin/gzip\
compressext .gz\
rotate 16\
}

cat logrotate_transcode

/home/ubuntu/temp/transcode.log {\
su ubuntu ubuntu\
dateext\
dateformat -%Y%m%d-%s\
copytruncate\
compress\
compresscmd /bin/gzip\
compressext .gz\
rotate 16\
}

cat logrotate_delayed

/home/ubuntu/temp/delayed.log {\
su ubuntu ubuntu\
dateext\
dateformat -%Y%m%d-%s\
copytruncate\
compress\
compresscmd /bin/gzip\
compressext .gz\
rotate 16\
}

**3)Edit crontab.**

crontab -e

\# Edit this file to introduce tasks to be run by cron.\
\#\
\# Each task to run has to be defined through a single line\
\# indicating with different fields when the task will be run\
\# and what command to run for the task\
\#\
\# To define the time you can provide concrete values for\
\# minute (m), hour (h), day of month (dom), month (mon),\
\# and day of week (dow) or use \'\*\' in these fields (for \'any\').\
\#\
\# Notice that tasks will be started based on the cron\'s system\
\# daemon\'s notion of time and timezones.\
\#\
\# Output of the crontab jobs (including errors) is sent through\
\# email to the user the crontab file belongs to (unless redirected).\
\#\
\# For example, you can run a backup of all your user accounts\
\# at 5 a.m every week with:\
\# 0 5 \* \* 1 tar -zcf /var/backups/home.tgz /home/\
\#\
\# For more information see the manual pages of crontab(5) and cron(8)\
\#\
\# m h dom mon dow command

- \* \* \* \* /home/ubuntu/text_collector_script/processed_data.sh

- \* \* \* \* /home/ubuntu/text_collector_script/transcoded_size.sh

- \* \* \* \* /home/ubuntu/text_collector_script/transcoding_times.sh

- \* \* \* \* /home/ubuntu/text_collector_script/transcoding_extras.sh

#1 6,12,18,23 \* \* \* /usr/sbin/logrotate -f
/etc/logrotate.d/logrotate_transcode \> /tmp/logrotate.log 2\>&1\
#1 6,12,18,23 \* \* \* /usr/sbin/logrotate -f
/etc/logrotate.d/logrotate_delayed \> /tmp/logrotate_delayed.log 2\>&1\
#\*/3 \* \* \* \* cd /home/ubuntu/log_push_s3/ && /usr/bin/bash
logs_push_s3.sh\
11 6,12,18,23 \* \* \* sh /home/ubuntu/log_push_s3/logs_push_s3.sh

**4)Setup logrotate and s3 push.**

mkdir /home/ubuntu/log_push_s3

cat /home/ubuntu/log_push_s3/logs_push_s3.sh

#!/bin/bash\
/usr/sbin/logrotate -f /etc/logrotate.d/logrotate_transcode \>
/tmp/logrotate.log 2\>&1\
/usr/sbin/logrotate -f /etc/logrotate.d/logrotate_delayed \>
/tmp/logrotate_delayed.log 2\>&1\
/usr/sbin/logrotate -f /etc/logrotate.d/logrotate_ffmpeg \>
/tmp/logrotate_delayed.log 2\>&1\
dateoriginal=\`date +%Y%m%d\`\
host=\`hostname\`\
ip=\`hostname -i\`

S3_PATH=ugc-prod-logs/josh-transcode-service/josh-transcode-h265_m3u8\
LOGS_PATH=/home/ubuntu/temp\
ls /home/ubuntu/temp/\*\"\$dateoriginal\"\* \> /tmp/list

while IFS= read -r line\
do\
/usr/local/bin/aws s3 cp \$line
s3://\${S3_PATH}/\${dateoriginal}/\${ip}/ \--region ap-south-1\
done \< /tmp/list

chmod +x /home/ubuntu/log_push_s3/logs_push_s3.sh

**5)Setup delayed_process service.**

cat /home/ubuntu/delayed_process.sh\
while true\
do\
\> /tmp/delayed.log\
#chown ubuntu:ubuntu /home/ubuntu/temp/delayed.log\
#chown ubuntu:ubuntu /tmp/delayed.log\
#chmod 777 /home/ubuntu/temp/delayed.log\
#chmod 777 /tmp/delayed.log\
ps -ef \| grep ffmpeg \| grep -v worker \| grep -v grep \| awk \'{print
\$2 \" \" \$7}\' \| cut -d \':\' -f-2 \> /tmp/process.txt\
while IFS= read -r line\
do\
pid=\$(echo \$line \| awk \'{print \$1}\')\
minute=\$(echo \$line \| cut -d \':\' -f2 \| sed \'s/\^0\*//\')\
if \[\[ \$minute -ge 15 \]\]; then\
kill -9 \"\$pid\"\
time=\$(date +\"%Y-%m-%dT%H:%M\")\
process=\$(ps -ef \| grep \"\$pid\" \| grep -v grep)\
echo \"\*\$time\* \$process\" \>\> /home/ubuntu/temp/delayed.log\
echo \"\*\$time\* \$process\" \>\> /tmp/delayed.log\
fi\
done \< /tmp/process.txt\
#Prometheus Push\
\> /var/lib/node_exporter/textfile_collector/delayed_process.prom\
#time=\$(date +\"%Y-%m-%dT%H:%M\")\
data=\$(cat /tmp/delayed.log \| wc -l)\
bash -c \"echo \'delayed_process{kind=\\\"H265_M3U8\\\"} \$data\' \>\>
/var/lib/node_exporter/textfile_collector/delayed_process.prom\"\
echo \"Sleeping for 1 minute.\"\
sleep 1m\
done

chmod +x /home/ubuntu/delayed_process.sh

cat /usr/lib/systemd/system/delayed_process.service\
\[Unit\]\
Description=delayed_process

\[Service\]\
user=ubuntu\
group=ubuntu\
ExecStart=/bin/bash /home/ubuntu/delayed_process.sh

\[Install\]\
WantedBy=multi-user.target

systemctl start delayed_process

systemctl enable delayed_process

**6)Setup lifecycle hook.**

cat /home/ubuntu/lifecycle.sh\
cond=\$(hostname)\
if \[\[ \$cond -eq \"ip-10-10-49-152\" \]\]; then\
exit 0\
fi\
while true\
do\
lifecycle=\$(aws autoscaling describe-auto-scaling-groups
\--auto-scaling-group-names
Josh-Transcode-h265_m3u8-visionular-autoscale \--query
\'AutoScalingGroups\[\].Instances\[\].\[InstanceId,LifecycleState\]\'
\--output text \| grep \$(ec2metadata \--instance-id) \| awk \'{print
\$2}\')\
echo \$lifecycle \> /home/ubuntu/lifecycle\
sleep 30\
done

chmod +x /home/ubuntu/lifecycle.sh

cat /usr/lib/systemd/system/lifecycle.service\
\[Unit\]\
Description=Lifecycle

\[Service\]\
ExecStart=/bin/bash /home/ubuntu/lifecycle.sh

\[Install\]\
WantedBy=multi-user.target

systemctl start lifecycle

systemctl enable lifecycle

**7)Add prometheus data push scripts.**

cat /home/ubuntu/text_collector_script/processed_data.sh\
#!/bin/bash\
date12=\$(date +\"%Y-%m-%d %H:%M\" \--date \'now - 1 minutes\')\
processed_false=\$(cat /home/ubuntu/temp/transcode.log \| grep -i
\"\$date12\" \| grep -o -i \'processed\": false\' \| wc -l)\
processed_true=\$(cat /home/ubuntu/temp/transcode.log \| grep -i
\"\$date12\" \| grep -o -i \'processed\": true\' \| wc -l)

H265_M3U8_average_time_per_min=\$(cat /home/ubuntu/temp/transcode.log \|
grep -i \"\$date12\" \| grep -i time_taken \| grep -i \'kind\":
\"H265_M3U8\' \| grep -E -o \"time_taken.{0,8}\" \| sed
\'s/\[\^0-9\]\*//g\' \| awk \'{total+= \$1; count++} END {print
total/count}\')

#HLS_average_file_size=\$(cat /home/ubuntu/temp/transcode.log \| grep -i
\"\$date12\" \| grep -i file_size \| grep -i \'kind\": \"HLS\' \| grep
-E -o \"file_size.{0,15}\"\| sed \'s/\[\^0-9\]\*//g\' \| awk \'{total+=
\$1; count++} END {print total/count/1024/1024}\')

#HLS_average_bitrate=\$(cat /home/ubuntu/temp/transcode.log \| grep -i
\"\$date12\" \| grep -i bitrate \| grep -i \'kind\": \"HLS\' \| grep -E
-o \"bitrate.{0,10}\"\| sed \'s/\[\^0-9.\]\*//g\' \| awk \'{total+= \$1;
count++} END {print total/count}\')

#HLS_average_video_duration=\$(cat /home/ubuntu/temp/transcode.log \|
grep -i \"\$date12\" \| grep -i video_duration \| grep -i \'kind\":
\"HLS\' \| grep -E -o \"video_duration.{0,10}\"\| sed
\'s/\[\^0-9.\]\*//g\' \| awk \'{total+= \$1; count++} END {print
total/count}\')

#HLS_average_turnaround_time_per_min=\$(cat
/home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
turnaround_time \| grep -i \'kind\": \"HLS\' \| grep -E -o
\"turnaround_time.{0,8}\" \| sed \'s/\[\^0-9\]\*//g\' \| awk \'{total+=
\$1; count++} END {print total/count}\')

echo \"h265_m3u8_processed_false \$processed_false\" \>
/var/lib/node_exporter/processed_data.prom.\$\$\
echo \"h265_m3u8_processed_true \$processed_true\" \>\>
/var/lib/node_exporter/processed_data.prom.\$\$

#echo \"HLS_average_file_size \$HLS_average_file_size\" \>\>
/var/lib/node_exporter/processed_data.prom.\$\$\
#echo \"HLS_average_bitrate \$HLS_average_bitrate\" \>\>
/var/lib/node_exporter/processed_data.prom.\$\$\
#echo \"HLS_average_video_duration \$HLS_average_video_duration\" \>\>
/var/lib/node_exporter/processed_data.prom.\$\$\
#echo \"HLS_average_turnaround_time_per_min
\$HLS_average_turnaround_time_per_min\" \>\>
/var/lib/node_exporter/processed_data.prom.\$\$

#echo \"hls_average_time_per_min \$HLS_average_time_per_min\" \>\>
/var/lib/node_exporter/processed_data.prom.\$\$

mv /var/lib/node_exporter/processed_data.prom.\$\$
/var/lib/node_exporter/textfile_collector/processed_data.prom

cat /home/ubuntu/text_collector_script/transcoded_size.sh\
#!/bin/bash\
date12=\$(date +\"%Y-%m-%d %H:%M\" \--date \'now - 1 minutes\')

\> /var/lib/node_exporter/textfile_collector/processedsize.prom\
#File Name\
#cat /home/ubuntu/temp/transcode.log \| grep \"hls_transcoded_size\" \|
grep -i \"\$date12\" \| cut -d\",\" -f1 \| cut -d\"\'\" -f4 \>
/home/ubuntu/text_collector_script/fname

#l Type\
cat /home/ubuntu/temp/transcode.log \| grep
\"h265_m3u8_transcoded_size\" \| grep -i \"\$date12\" \| tr -d \" \'\"
\| cut -d\"}\" -f1 \| cut -d\"{\" -f3 \| grep \'\\S\' \| cut -d\",\" -f1
\| cut -d\":\" -f2 \| sed -e \'s/\^\$/0/\' \>
/home/ubuntu/text_collector_script/ltype

#m Type\
cat /home/ubuntu/temp/transcode.log \| grep
\"h265_m3u8_transcoded_size\" \| grep -i \"\$date12\" \| tr -d \" \'\"
\| cut -d\"}\" -f1 \| cut -d\"{\" -f3 \| grep \'\\S\' \| cut -d\",\" -f2
\| cut -d\":\" -f2 \| sed -e \'s/\^\$/0/\' \>
/home/ubuntu/text_collector_script/mtype

#h Type\
cat /home/ubuntu/temp/transcode.log \| grep
\"h265_m3u8_transcoded_size\" \| grep -i \"\$date12\" \| tr -d \" \'\"
\| cut -d\"}\" -f1 \| cut -d\"{\" -f3 \| grep \'\\S\' \| cut -d\",\" -f3
\| cut -d\":\" -f2 \| sed -e \'s/\^\$/0/\' \>
/home/ubuntu/text_collector_script/htype

#vh Type\
cat /home/ubuntu/temp/transcode.log \| grep
\"h265_m3u8_transcoded_size\" \| grep -i \"\$date12\" \| tr -d \" \'\"
\| cut -d\"}\" -f1 \| cut -d\"{\" -f3 \| grep \'\\S\' \| cut -d\",\" -f4
\| cut -d\":\" -f2 \| sed -e \'s/\^\$/0/\' \>
/home/ubuntu/text_collector_script/vhtype

line_number=0\
while read -u 3 -r ltype && read -u 4 -r mtype && read -u 5 -r htype &&
read -u 6 -r vhtype; do\
line_number=\$(( \$line_number + 1 ))\
echo
\"transcoding_size{video_kind=\\\"H265_M3U8\\\",type=\\\"l\\\",filename=\\\"\$line_number\\\"}
\$ltype\" \>\>
/var/lib/node_exporter/textfile_collector/processedsize.prom\
echo
\"transcoding_size{video_kind=\\\"H265_M3U8\\\",type=\\\"m\\\",filename=\\\"\$line_number\\\"}
\$mtype\" \>\>
/var/lib/node_exporter/textfile_collector/processedsize.prom\
echo
\"transcoding_size{video_kind=\\\"H265_M3U8\\\",type=\\\"h\\\",filename=\\\"\$line_number\\\"}
\$htype\" \>\>
/var/lib/node_exporter/textfile_collector/processedsize.prom\
echo
\"transcoding_size{video_kind=\\\"H265_M3U8\\\",type=\\\"vh\\\",filename=\\\"\$line_number\\\"}
\$vhtype\" \>\>
/var/lib/node_exporter/textfile_collector/processedsize.prom\
done 3\</home/ubuntu/text_collector_script/ltype
4\</home/ubuntu/text_collector_script/mtype
5\</home/ubuntu/text_collector_script/htype
6\</home/ubuntu/text_collector_script/vhtype

cat /home/ubuntu/text_collector_script/transcoding_times.sh\
#!/bin/bash\
date12=\$(date +\"%Y-%m-%d %H:%M\" \--date \'now - 1 minutes\')\
#date13=\$(date +\"%Y-%m-%d %H:%M\" \--date \'now - 2 minutes\')\
#date12=\${date12:: -1}\
\> /var/lib/node_exporter/textfile_collector/finalprocessingtime.prom

#Content UUID\
#cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
time_taken \| grep -i \'kind\": \"MP4\' \| grep -E -o
\"content_uuid.{0,41}\" \| cut -d\":\" -f2 \| tr -d \'\" \' \>
/home/ubuntu/text_collector_script/cuuid

#Processing Time\
cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
time_taken \| grep -i \'kind\": \"H265_M3U8\' \| grep -E -o
\"time_taken.{0,9}\" \| sed \'s/\[\^0-9\]\*//g\' \| tr -d \"}\" \>
/home/ubuntu/text_collector_script/finalptime

#S3 Upload Time\
#cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
time_taken \| grep -i \'kind\": \"HLS\' \| grep -E -o
\"s3_upload_time.{0,9}\" \| cut -d\":\" -f2 \| tr -d \' ,\"\' \>
/home/ubuntu/text_collector_script/finals3utime

#S3 Download Time\
#cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
time_taken \| grep -i \'kind\": \"HLS\' \| grep -E -o
\"s3_download_time.{0,9}\" \| tr -d \'\" \' \| cut -d\":\" -f2 \| tr -d
\",\" \> /home/ubuntu/text_collector_script/finals3dtime

#API Time\
#cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
time_taken \| grep -i \'kind\": \"HLS\' \| grep -E -o
\"api_time_in_ms.{0,9}\" \| cut -d\":\" -f2 \| tr -d \' ,}\' \>
/home/ubuntu/text_collector_script/finalapitime

#Turnaround Time\
#cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
time_taken \| grep -i \'kind\": \"HLS\' \| grep -E -o
\"turnaround_time.{0,9}\" \| sed \'s/\[\^0-9\]\*//g\' \| tr -d \'}\' \>
/home/ubuntu/text_collector_script/finaltatime

#cat /home/ubuntu/text_collector_script/finaltatime

line_number=0\
while read -u 3 -r ptime; do\
#&& read -u 4 -r tatime && read -u 5 -r apitime; do\
line_number=\$(( \$line_number + 1 ))\
echo
\"transcoding_video_time{video_kind=\\\"H265_M3U8\\\",type=\\\"processing\\\",uuid=\\\"\$line_number\\\"}
\$ptime\" \>\>
/var/lib/node_exporter/textfile_collector/finalprocessingtime.prom\
#echo
\"transcoding_video_time{video_kind=\\\"HLS\\\",type=\\\"s3_upload\\\",uuid=\\\"\$line_number\\\"}
\$s3utime\" \>\>
/var/lib/node_exporter/textfile_collector/finalprocessingtime.prom\
#echo
\"transcoding_video_time{video_kind=\\\"HLS\\\",type=\\\"s3_download\\\",uuid=\\\"\$line_number\\\"}
\$s3dtime\" \>\>
/var/lib/node_exporter/textfile_collector/finalprocessingtime.prom\
#echo
\"transcoding_video_time{video_kind=\\\"HLS\\\",type=\\\"api\\\",uuid=\\\"\$line_number\\\"}
\$apitime\" \>\>
/var/lib/node_exporter/textfile_collector/finalprocessingtime.prom\
#echo
\"transcoding_video_time{video_kind=\\\"HLS\\\",type=\\\"turnaround\\\",uuid=\\\"\$line_number\\\"}
\$tatime\" \>\>
/var/lib/node_exporter/textfile_collector/finalprocessingtime.prom\
#echo \"MP4_processing_time{uuid=\\\"\$line2\\\"} \$line1\" \>\>
/var/lib/node_exporter/textfile_collector/processingtime.prom\
done 3\</home/ubuntu/text_collector_script/finalptime\
#4\</home/ubuntu/text_collector_script/finaltatime
5\</home/ubuntu/text_collector_script/finalapitime\
#6\</home/ubuntu/text_collector_script/finals3utime
7\</home/ubuntu/text_collector_script/finals3dtime

cat /home/ubuntu/text_collector_script/transcoding_extras.sh\
#!/bin/bash\
date12=\$(date +\"%Y-%m-%d %H:%M\" \--date \'now - 1 minutes\')

\> /var/lib/node_exporter/textfile_collector/durationbitrate.prom

#Video Duration\
cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
video_duration \| grep -i \'kind\": \"H265_M3U8\' \| grep -E -o
\"video_duration.{0,11}\" \| sed \'s/\[\^0-9.\]\*//g\' \>
/home/ubuntu/text_collector_script/videoduration

#Bitrate\
cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
\'kind\": \"H265_M3U8\' \| grep -i bitrate \| grep -E -o
\'bitrate\":.{0,10}\' \| sed \'s/\[\^0-9.\]\*//g\' \>
/home/ubuntu/text_collector_script/bitrate

#Original File Size\
cat /home/ubuntu/temp/transcode.log \| grep -i \"\$date12\" \| grep -i
file_size \| grep -i \'kind\": \"H265_M3U8\' \| grep -E -o
\"file_size.{0,15}\" \| sed \'s/\[\^0-9\]\*//g\' \>
/home/ubuntu/text_collector_script/filesize

line_number=0\
while read -u 3 -r duration && read -u 4 -r bitrate && read -u 5 -r
filesize; do\
line_number=\$(( \$line_number + 1 ))\
echo
\"transcoding_video_original_size{video_kind=\\\"H265_M3U8\\\",filename=\\\"\$line_number\\\"}
\$filesize\" \>\>
/var/lib/node_exporter/textfile_collector/durationbitrate.prom\
echo
\"transcoding_video_duration{video_kind=\\\"H265_M3U8\\\",filename=\\\"\$line_number\\\"}
\$duration\" \>\>
/var/lib/node_exporter/textfile_collector/durationbitrate.prom\
echo
\"transcoding_video_bitrate{video_kind=\\\"H265_M3U8\\\",filename=\\\"\$line_number\\\"}
\$bitrate\" \>\>
/var/lib/node_exporter/textfile_collector/durationbitrate.prom\
done 3\</home/ubuntu/text_collector_script/videoduration
4\</home/ubuntu/text_collector_script/bitrate
5\</home/ubuntu/text_collector_script/filesize

chmod +x /home/ubuntu/text_collector_script/\*.sh

**8)Add rc.local entry.**

cat /etc/rc.local

#!/bin/sh -e\
\#\
\# rc.local\
\#\
\# This script is executed at the end of each multiuser runlevel.\
\# Make sure that the script will \"exit 0\" on success or any other\
\# value on error.\
\#\
\# In order to enable or disable this script just change the execution\
\# bits.\
\#\
\# By default this script does nothing.

/bin/bash /root/clear_db.sh\
exit 0

chmod +x /etc/rc.local

cat /root/clear_db.sh

cond=\$(hostname)\
if \[\[ \$cond -ne \"ip-10-10-49-152\" \]\]; then\
rm -rf /var/lib/node_exporter/textfile_collector/\*.db\
fi

chmod +x /root/clear_db.sh

systemctl start rc-local

**9)Full permission to textfile_collector folder.**

chmod 777 /var/lib/node_exporter/textfile_collector

**Additional Steps for specific codecs -**\
\
`apt-get install libaom-devel`\
\
For libx264 -\
\
`./configure --prefix=/usr --enable-gpl --enable-version3 --enable-libfdk_aac --enable-libmp3lame --enable-libtheora --enable-libvpx --enable-libx264 --enable-nonfree --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libxvid --enable-libwebp --enable-static --enable-libfreetype`\
\
For libx265 -\
\
`./configure --prefix=/usr --enable-gpl --enable-version3 --enable-libfdk_aac --enable-libmp3lame --enable-libtheora --enable-libvpx --enable-libx265 --enable-nonfree --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libxvid --enable-libwebp --enable-static --enable-libfreetype`\

\~ **Abhimanyu Singhal**
