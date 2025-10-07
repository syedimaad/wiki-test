All team members should provide their priorities, progress, and problems
each day in this report.

  ----------------------- -------------
  **Team name**           \@Transcode
  **Direct supervisor**   
  **Table of contents**   17pipe
  ----------------------- -------------

##  Friday [01-04-2022]{style="color: rgb(0,184,217);"}

+---+-----------------+------------+------------------+-------------------+
|   | **Name**        | **Owner**  | **Progress**     | **Status**        |
+---+-----------------+------------+------------------+-------------------+
| 1 | HLS deployment  |            | - Infra          | Done              |
|   |                 |            |   dependency     |                   |
|   |                 |            |                  |                   |
|   |                 |            | - log push to S3 |                   |
+---+-----------------+------------+------------------+-------------------+
| 2 | Bulk HLS        |            | - code changes   | Done              |
|   | deployment with |            |   as per Bulk    |                   |
|   | Visionular      |            |   with           |                   |
|   |                 |            |                  |                   |
|   |                 |            | - HLS(H265+H264) |                   |
|   |                 |            |   with           |                   |
|   |                 |            |   visionular     |                   |
|   |                 |            |                  |                   |
|   |                 |            | - Create new     |                   |
|   |                 |            |   Instance from  |                   |
|   |                 |            |   H264(WZ) AMI   |                   |
|   |                 |            |   for Bulk       |                   |
|   |                 |            |                  |                   |
|   |                 |            | - Monitor        |                   |
|   |                 |            |                  |                   |
|   |                 |            | - Create New ASG |                   |
|   |                 |            |   with           |                   |
|   |                 |            |   visionular     |                   |
|   |                 |            |                  |                   |
|   |                 |            | - rollout 10%    |                   |
|   |                 |            |   for some       |                   |
|   |                 |            |   time + monitor |                   |
|   |                 |            |                  |                   |
|   |                 |            | - rollout 100% + |                   |
|   |                 |            |   monitor        |                   |
+---+-----------------+------------+------------------+-------------------+
| 3 | Creator         |            | - Debugging      |                   |
|   | escalations     |            |                  |                   |
+---+-----------------+------------+------------------+-------------------+
| 4 | Image           |            | - Try to get     | - All AudioImages |
|   | optimization    |            |   userID by      |   transcoded      |
|   |                 |            |   image, check   |                   |
|   |                 |            |   with Ruchi     | - Transcoded      |
|   |                 |            |                  |   popular         |
|   |                 |            | - Same applies   |   userProfile     |
|   |                 |            |   for Audio      |   pictures        |
|   |                 |            |   Image          |                   |
|   |                 |            |                  | - AudioExtract    |
|   |                 |            | - Check with CMS |   with            |
|   |                 |            |   team about     |   UserProfileIcon |
|   |                 |            |   original image |   is not getting  |
|   |                 |            |   direct access  |   assignd with    |
|   |                 |            |                  |   transcoding     |
|   |                 |            |                  |   version         |
+---+-----------------+------------+------------------+-------------------+
| 5 | - VideoPlay vs  |            | - Take the steps |                   |
|   |   PageViews     |            |   that discussed |                   |
|   |   gaps          |            |   in other RCA   |                   |
|   |                 |            |   Notification   |                   |
|   | - Notification  |            |   Sheet          |                   |
|   |   click vs Play |            |                  |                   |
|   |   gaps          |            |                  |                   |
+---+-----------------+------------+------------------+-------------------+

##  Thursday [31-03-2022]{style="color: rgb(0,184,217);"}

+---+-----------------+------------+-----------------+-----------------+
|   | **Name**        | **Owner**  | **Progress**    | **Problems**    |
+---+-----------------+------------+-----------------+-----------------+
| 1 | - VideoPlay vs  |            | Should be       | 31-03-2022      |
|   |   PageViews     |            | closed today    |                 |
|   |   gaps          |            |                 |                 |
|   |                 |            |                 |                 |
|   | - Notification  |            |                 |                 |
|   |   click vs Play |            |                 |                 |
|   |   gaps          |            |                 |                 |
+---+-----------------+------------+-----------------+-----------------+
| 2 | H264 HLS        |            | - reduce        |                 |
|   | deployment with |            |   concurrency   |                 |
|   | Visionular      |            |   to 19         |                 |
|   |                 |            |                 |                 |
|   |                 |            | - create AMI    |                 |
|   |                 |            |                 |                 |
|   |                 |            | - ASG rollout   |                 |
|   |                 |            |                 |                 |
|   |                 |            | - Monitoring    |                 |
+---+-----------------+------------+-----------------+-----------------+
| 3 | Back populate   | p1         | - Collect       | Done            |
|   | popular videos  |            |   poppular      |                 |
|   | audio into      |            |   videos        |                 |
|   | FingerPrint     |            |   viewCount \>  |                 |
|   | service         |            |   1000          |                 |
|   |                 |            |                 |                 |
|   |                 |            | - Collect       |                 |
|   |                 |            |   unique audios |                 |
|   |                 |            |   and filter    |                 |
|   |                 |            |   out the       |                 |
|   |                 |            |   audios never  |                 |
|   |                 |            |   passed        |                 |
|   |                 |            |   through       |                 |
|   |                 |            |   clustering &  |                 |
|   |                 |            |   meta          |                 |
|   |                 |            |   extraction    |                 |
|   |                 |            |                 |                 |
|   |                 |            | - then push to  |                 |
|   |                 |            |   stream        |                 |
+---+-----------------+------------+-----------------+-----------------+
| 4 | Creator         | p0         |                 |                 |
|   | escalations     |            |                 |                 |
+---+-----------------+------------+-----------------+-----------------+
| 5 | Retranscode     | p2         | - push the      | Done            |
|   | popular videos  |            |   videos        |                 |
|   |                 |            |   according to  |                 |
|   |                 |            |   load of H265  |                 |
|   |                 |            |                 |                 |
|   |                 |            | <!-- -->        |                 |
|   |                 |            |                 |                 |
|   |                 |            | - To fast       |                 |
|   |                 |            |   process,      |                 |
|   |                 |            |   increase      |                 |
|   |                 |            |   desired       |                 |
|   |                 |            |   instances     |                 |
|   |                 |            |                 |                 |
|   |                 |            | - then revert   |                 |
+---+-----------------+------------+-----------------+-----------------+
| 6 | Image           | p3         | - Data received |                 |
|   | optimization    |            |   from CDN      |                 |
|   |                 |            |                 |                 |
|   |                 |            | - Analyse the   |                 |
|   |                 |            |   data and push |                 |
|   |                 |            |   for           |                 |
|   |                 |            |   transcoding   |                 |
+---+-----------------+------------+-----------------+-----------------+
| 7 | check whether   | p0         | - Check ES &    | Done            |
|   | duration_ms     |            |   Dynamo entry  |                 |
|   | field is        |            |                 |                 |
|   | populating      |            |                 |                 |
|   | proper from     |            |                 |                 |
|   | Music & Audio   |            |                 |                 |
|   | transcoding     |            |                 |                 |
+---+-----------------+------------+-----------------+-----------------+

##  Wednesday [30-03-2022]{style="color: rgb(0,184,217);"}

+---+-------------------+------------+------------------------------------------+------------+
|   | **Name**          | **Owner**  | **Progress**                             | **ETA**    |
+---+-------------------+------------+------------------------------------------+------------+
| 1 | H264 HLS          |            | - Take instance from H265 AMI            | 30-03-2022 |
|   | deployment with   |            |                                          |            |
|   | Visionular        |            | - cross check ffmpeg paths in code and   |            |
|   |                   |            |   shell                                  |            |
|   |                   |            |                                          |            |
|   |                   |            | - Deploy code base to prod               |            |
|   |                   |            |                                          |            |
|   |                   |            | - Monitor closely                        |            |
|   |                   |            |                                          |            |
|   |                   |            | - Create AMI and update ASG              |            |
+---+-------------------+------------+------------------------------------------+------------+
| 2 | H264 Bulk         |            | - Same steps of H264                     | 30-03-2022 |
|   | deployment with   |            |                                          |            |
|   | visionular        |            |                                          |            |
+---+-------------------+------------+------------------------------------------+------------+
| 3 | - VideoPlay vs    |            | [\<NOT                                   | 30-03-2022 |
|   |   PageViews gaps  |            | DONE\>]{style="color: rgb(255,86,48);"}  |            |
|   |                   |            |                                          |            |
|   | - Notification    |            | [occupied in HLS H264                    |            |
|   |   click vs Play   |            | rollout]{style="color: rgb(255,86,48);"} |            |
|   |   gaps            |            |                                          |            |
+---+-------------------+------------+------------------------------------------+------------+
| 4 |                   |            |                                          |            |
+---+-------------------+------------+------------------------------------------+------------+
| 5 |                   |            |                                          |            |
+---+-------------------+------------+------------------------------------------+------------+
| 6 |                   |            |                                          |            |
+---+-------------------+------------+------------------------------------------+------------+

##  Tuesday [29-03-2022]{style="color: rgb(0,184,217);"}

+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
|   | **Name**      | **Owner**                     | **Progress**   | **EOD Update**                              | **ETA**    |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
| 1 | Visionular    | 1 complete                    | - development  | - Merged by Nagesh                          | 2022-03-29 |
|   | rollout to    | []{.placeholder-inline-tasks} |   in progress  |                                             |            |
|   | H264          |                               |                | - Tested in dev environment                 |            |
|   |               |                               | - Cover bulk   |                                             |            |
|   |               |                               |   flow too     |                                             |            |
|   |               |                               |                |                                             |            |
|   |               |                               | - Testing to   |                                             |            |
|   |               |                               |   be done end  |                                             |            |
|   |               |                               |   to end       |                                             |            |
|   |               |                               |                |                                             |            |
|   |               |                               | - Review by    |                                             |            |
|   |               |                               |                |                                             |            |
|   |               |                               | - Code merge   |                                             |            |
|   |               |                               |   by           |                                             |            |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
| 2 | Retranscode   |                               | - Do manually  | - running on slow rate                      | 2022-03-29 |
|   | popular       |                               |   this time    |                                             |            |
|   | videos        |                               |   for H265     |                                             |            |
|   |               |                               |                |                                             |            |
|   | Image         |                               | - viewCount \> |                                             |            |
|   | optimization  |                               |   1000         |                                             |            |
|   |               |                               |                |                                             |            |
|   |               |                               | - get data     |                                             |            |
|   |               |                               |   from CDN and |                                             |            |
|   |               |                               |   transcode    |                                             |            |
|   |               |                               |   them         |                                             |            |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
| 3 | - Grafana     |                               | - stream       | - [\<NO                                     | 2022-03-29 |
|   |   gaps        |                               |   retranscode  |   UPDATE\>]{style="color: rgb(255,86,48);"} |            |
|   |               |                               |   seeing some  |                                             |            |
|   | - All reports |                               |   gaps         |                                             |            |
|   |   integration |                               |                |                                             |            |
|   |   &           |                               | - Bulk TAT is  |                                             |            |
|   |   Retranscode |                               |   too high     |                                             |            |
|   |   proper      |                               |                |                                             |            |
|   |   setup       |                               | - check all    |                                             |            |
|   |               |                               |   kinds graph  |                                             |            |
|   |               |                               |   health       |                                             |            |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
| 4 | All Common    |                               | - integrate    | - received data from CDN team               |            |
|   | entity images |                               |   with CMS and |                                             |            |
|   | to be         |                               |   also analyse | - Yet to push to stream                     |            |
|   | transcoded    |                               |   are there    |                                             |            |
|   | before        |                               |   any images   |                                             |            |
|   | publish       |                               |   serving      |                                             |            |
|   |               |                               |   directly     |                                             |            |
|   |               |                               |   other than   |                                             |            |
|   |               |                               |   CMS          |                                             |            |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
| 5 | Notification  |                               | - Seeing       | - Analysis in progress                      | 2022-03-29 |
|   | click vs Play |                               |   notification |                                             |            |
|   | gaps          |                               |   click vs     | - Spilled over                              |            |
|   |               |                               |   Video play   |                                             |            |
|   |               |                               |   having high  |                                             |            |
|   |               |                               |   difference,  |                                             |            |
|   |               |                               |   analyse the  |                                             |            |
|   |               |                               |   reason       |                                             |            |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+
| 6 | VideoPlay vs  |                               | - Thushar      | - Analysis in progress                      | 2022-03-29 |
|   | PageViews     |                               |   generates    |                                             |            |
|   | gaps          |                               |   these events | - Spilled over                              |            |
|   |               |                               |                |                                             |            |
|   |               |                               | - Ask Client   |                                             |            |
|   |               |                               |   team about   |                                             |            |
|   |               |                               |   gaps(when    |                                             |            |
|   |               |                               |   event will   |                                             |            |
|   |               |                               |   be triggered |                                             |            |
|   |               |                               |   from page    |                                             |            |
|   |               |                               |   view to      |                                             |            |
|   |               |                               |   video play)  |                                             |            |
|   |               |                               |                |                                             |            |
|   |               |                               | - if video     |                                             |            |
|   |               |                               |   unable to    |                                             |            |
|   |               |                               |   play, any    |                                             |            |
|   |               |                               |   events to    |                                             |            |
|   |               |                               |   analyse,     |                                             |            |
|   |               |                               |   check with   |                                             |            |
|   |               |                               |   client team  |                                             |            |
+---+---------------+-------------------------------+----------------+---------------------------------------------+------------+

##  Monday [04-04-2022]{style="color: rgb(0,184,217);"}

+---+----------------+-----------------+-------------------+---------------+
|   | **Name**       | **Priorities**  | **Progress**      | **ETA**       |
+---+----------------+-----------------+-------------------+---------------+
| 1 | Image          |                 | - Enable          | e.g.,         |
|   | optimization   |                 |   Transcoding for | Customer      |
|   |                |                 |   all static      | hasn\'t       |
|   |                |                 |   images          | returned      |
|   |                |                 |                   | email about   |
|   |                |                 | - Fix the         | moving        |
|   |                |                 |   userProfileIcon | forward       |
|   |                |                 |   non transcoding |               |
|   |                |                 |   version for     |               |
|   |                |                 |   AudioImages     |               |
|   |                |                 |                   |               |
|   |                |                 | e.g., Waiting on  |               |
|   |                |                 | final input for   |               |
|   |                |                 | project plan      |               |
+---+----------------+-----------------+-------------------+---------------+
| 2 | Visionular AV1 |                 | - Integrate AV1   |               |
|   | experiment     |                 |                   |               |
|   |                |                 | - create          |               |
|   |                |                 |   documentation   |               |
+---+----------------+-----------------+-------------------+---------------+
| 3 | Visionular     |                 | - Check Queue     |               |
|   | Deployment     |                 |   registration    |               |
|   |                |                 |                   |               |
|   | Kinds          |                 | - upscale         |               |
|   | deployment     |                 |   downscale       |               |
|   |                |                 |   policies        |               |
|   |                |                 |                   |               |
|   |                |                 | - etc             |               |
+---+----------------+-----------------+-------------------+---------------+
| 4 | MP4 visionular |                 | - Share some      |               |
|   | integration    |                 |   samples to Hive |               |
|   |                |                 |   team for any    |               |
|   |                |                 |   issues          |               |
+---+----------------+-----------------+-------------------+---------------+
| 5 | VideoPlay vs   |                 |                   |               |
|   | PageViews gaps |                 |                   |               |
|   |                |                 |                   |               |
|   | - Notification |                 |                   |               |
|   |   click vs     |                 |                   |               |
|   |   Play gaps    |                 |                   |               |
+---+----------------+-----------------+-------------------+---------------+
| 6 | Thumbnail load |                 |                   | 04-04-2022    |
|   | errors         |                 |                   |               |
+---+----------------+-----------------+-------------------+---------------+
