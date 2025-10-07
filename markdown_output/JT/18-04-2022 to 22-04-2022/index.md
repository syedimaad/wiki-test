All team members should provide their priorities, progress, and problems
each day in this report.

  ----------------------- -----------------------------
  **Team name**           @ mention team
  **Direct supervisor**   @ mention direct supervisor
  **Table of contents**   17pipe
  ----------------------- -----------------------------

##  Friday [22-04-2022]{style="color: rgb(0,184,217);"}

+---+----------------------+------------+---------------------+-----------------+
|   | **Name**             | **Owner**  | **Details**         | **ETA**         |
+---+----------------------+------------+---------------------+-----------------+
| 1 | terminate h265       |            | e.g., Waiting on    | e.g., Customer  |
|   | popular instances    |            | final input for     | hasn\'t         |
|   |                      |            | project plan        | returned email  |
|   |                      |            |                     | about moving    |
|   |                      |            |                     | forward         |
+---+----------------------+------------+---------------------+-----------------+
| 2 | Transcoding failures |            | - find the version  |                 |
|   | with AV1 codec       |            |   differences       |                 |
|   |                      |            |                     |                 |
|   |                      |            | - check the impact  |                 |
|   |                      |            |                     |                 |
|   |                      |            | - plan for upgrade  |                 |
|   |                      |            |   today/next week   |                 |
+---+----------------------+------------+---------------------+-----------------+
| 3 | SonarQube pending    |            | - take help of      |                 |
|   | kinds deployment     |            |   Awaneesh          |                 |
|   |                      |            |                     |                 |
|   |                      |            | - monitor and       |                 |
|   |                      |            |   understand every  |                 |
|   |                      |            |   step              |                 |
+---+----------------------+------------+---------------------+-----------------+
| 4 | WZ AV1 samples test  |            | - Data verification |                 |
|   |                      |            |   is done           |                 |
|   |                      |            |                     |                 |
|   |                      |            | - Quality testing   |                 |
|   |                      |            |   yet to be done    |                 |
|   |                      |            |                     |                 |
|   |                      |            | - Play in app and   |                 |
|   |                      |            |   observe the       |                 |
|   |                      |            |   decoding(ILT,BLT) |                 |
|   |                      |            |                     |                 |
|   |                      |            | - Publish all       |                 |
|   |                      |            |   observations      |                 |
|   |                      |            |   around AV1        |                 |
|   |                      |            |   serving           |                 |
+---+----------------------+------------+---------------------+-----------------+
| 5 | Dedup V2 deployment  |            | - Cleaned up data   |                 |
|   |                      |            |   due to issues at  |                 |
|   | - Producer script    |            |   Milvus            |                 |
|   |   based on Kinesis   |            |                     |                 |
|   |   iteratorAge(\>1hr) |            | - Check Milvus data |                 |
|   |                      |            |   & Monitoring end  |                 |
|   |                      |            |   to end            |                 |
+---+----------------------+------------+---------------------+-----------------+

##  Thursday [21-04-2022]{style="color: rgb(0,184,217);"}

  --- ---------------------------- ------------------------------- ----------------------------------------------- ------------------------------------------------------------
      **Name**                     **Priorities**                  **Progress**                                    **Problems** 
  1   Type @ to add user profile   e.g., Brainstorm budget ideas   e.g., Waiting on final input for project plan   e.g., Customer hasn\'t returned email about moving forward
  2                                                                                                                
  3                                                                                                                
  4                                                                                                                
  5                                                                                                                
  --- ---------------------------- ------------------------------- ----------------------------------------------- ------------------------------------------------------------

##  Wednesday [20-04-2022]{style="color: rgb(0,184,217);"}

+---+----------------------+-----------------+------------+---------------+----------+
|   | **Task**             | **Priorities**  | **Owner**  | **Details**   | **ETA**  |
+---+----------------------+-----------------+------------+---------------+----------+
| 1 | **Dedup V2           | P0              |            | - Test API    | Today    |
|   | deployment**         |                 |            |   changes in  |          |
|   |                      |                 |            |   stage       |          |
|   | - Producer for back  |                 |            |   before prod |          |
|   |   populate           |                 |            |               |          |
|   |                      |                 |            | - Push to     |          |
|   | - Producer script    |                 |            |   Reprocess   |          |
|   |   based on Kinesis   |                 |            |   Kinesis     |          |
|   |   iteratorAge(\>1hr) |                 |            |               |          |
|   |                      |                 |            | - Go slow in  |          |
|   |                      |                 |            |   producer    |          |
|   |                      |                 |            |   till        |          |
|   |                      |                 |            |   stabilizes\ |          |
|   |                      |                 |            |   starts with |          |
|   |                      |                 |            |   100 then    |          |
|   |                      |                 |            |   add zero    |          |
|   |                      |                 |            |   till 1L     |          |
+---+----------------------+-----------------+------------+---------------+----------+
| 2 | Left over deployment | P1              |            | - Pending:    | Tomorrow |
|   | of SonarQube         |                 |            |               |          |
|   | suggestions          |                 |            | - WMJ, HLS,   |          |
|   |                      |                 |            |   MP4,        |          |
|   |                      |                 |            |   THUMBNAIL   |          |
|   |                      |                 |            |               |          |
|   |                      |                 |            | - MUSIC       |          |
+---+----------------------+-----------------+------------+---------------+----------+
| 3 | Generate MP4 samples | P0              |            |               |          |
|   | with H264 WZ codec   |                 |            |               |          |
+---+----------------------+-----------------+------------+---------------+----------+
| 4 | **H265 MH into Good  | P0              |            |               | Today    |
|   | Profile changes and  |                 |            |               |          |
|   | deployment**         |                 |            |               |          |
+---+----------------------+-----------------+------------+---------------+----------+
| 5 | Bulk ASG right size  | P1              |            | - Problem:    | Today    |
|   |                      |                 |            |   downscale   |          |
|   |                      |                 |            |   is very     |          |
|   |                      |                 |            |   slow        |          |
|   |                      |                 |            |               |          |
|   |                      |                 |            | - for cost    |          |
|   |                      |                 |            |   cutting,    |          |
|   |                      |                 |            |   make little |          |
|   |                      |                 |            |   aggressive  |          |
|   |                      |                 |            |   in          |          |
|   |                      |                 |            |   downscale   |          |
|   |                      |                 |            |               |          |
|   |                      |                 |            | - 3mins drop  |          |
|   |                      |                 |            |   3 instances |          |
|   |                      |                 |            |   and monitor |          |
+---+----------------------+-----------------+------------+---------------+----------+
| 6 | Transcoding failures |                 |            | - Codec       | Today    |
|   | with AV1 codec       |                 |            |   unsupport   |          |
|   |                      |                 |            |   with AV1    |          |
+---+----------------------+-----------------+------------+---------------+----------+
| 7 | Copy betteraverage   | P0              |            |               | Today    |
|   | to good.m3u8         |                 |            |               |          |
+---+----------------------+-----------------+------------+---------------+----------+

##  Tuesday [19-04-2022]{style="color: rgb(0,184,217);"}

+---+---------------+-----------------+------------+----------+-------------+
|   | **Name**      | **Priorities**  | **Owner**  | **ETA**  | **Details** |
+---+---------------+-----------------+------------+----------+-------------+
| 1 | Dedup V2 Prod | P0              |            | tomorrow | - Exception |
|   | readiness     |                 |            |          |   handling  |
|   |               |                 |            |          |             |
|   |               |                 |            |          | - logic to  |
|   |               |                 |            |          |   cross     |
|   |               |                 |            |          |   check on  |
|   |               |                 |            |          |   dedup     |
|   |               |                 |            |          |   update    |
+---+---------------+-----------------+------------+----------+-------------+
| 2 | Left over     | P1              |            | NA       |             |
|   | deployment of |                 |            |          |             |
|   | SonarQube     |                 |            |          |             |
|   | suggestions   |                 |            |          |             |
+---+---------------+-----------------+------------+----------+-------------+
| 3 | Further       |                 |            | Today    |             |
|   | analysis on   |                 |            |          |             |
|   | high ILT &    |                 |            |          |             |
|   | BLT           |                 |            |          |             |
+---+---------------+-----------------+------------+----------+-------------+
| 4 | Transcoding & | P0              |            | Today    |             |
|   | Lambda health |                 |            |          |             |
+---+---------------+-----------------+------------+----------+-------------+
| 5 | Copy          |                 |            | Today    |             |
|   | betterAverage |                 |            |          |             |
|   | to good.m3u8  |                 |            |          |             |
+---+---------------+-----------------+------------+----------+-------------+

##  Monday [18-04-2022]{style="color: rgb(0,184,217);"}

  --- ---------------------------- ------------------------------- ----------------------------------------------- ------------------------------------------------------------
      **Name**                     **Priorities**                  **Progress**                                    **Problems** 
  1   Type @ to add user profile   e.g., Brainstorm budget ideas   e.g., Waiting on final input for project plan   e.g., Customer hasn\'t returned email about moving forward
  2                                                                                                                
  3                                                                                                                
  4                                                                                                                
  5                                                                                                                
  --- ---------------------------- ------------------------------- ----------------------------------------------- ------------------------------------------------------------
