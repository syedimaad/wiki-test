# Aim

The document aims at listing down the dev items needed to be done for
the Global Location Service for clients (Daedalus, AdEngine, Rico,
Content, etc) to fully migrate to Global Location Service

Josh → Santosh Kumar Kulkarni

Involve Tanvi confidence score and work on inhouse things in parallel

Training for IP based on Latitude and longitude

Catch up Bapu

  --------- -------------- --
  **Dev**   **Reviewer**   
                           
  --------- -------------- --

# Plan / Action Items

+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| **Item**    | **ETA (in      | **Status**    | **Use Case / | **Jira Link**                                            |
|             | days)**        |               | Priority**   |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Make city   | 12 May         | DoneGreen     | Content      |                                                          |
| Ids of      |                |               | Needs to     |                                                          |
| Global LS   |                |               | retain old   |                                                          |
| compatible  |                |               | Ids as they  |                                                          |
| with Old LS |                |               | maintain a   |                                                          |
|             |                |               | static       |                                                          |
|             |                |               | mapping of   |                                                          |
|             |                |               | Ids          |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Improve the | 31st May for   | DoneGreen     | (need to     | NHADSPLTL-4638e55da6ef-1840-3475-9293-310ba48d502dSystem |
| accuracy of | phase one      |               | learn over   | JIRA                                                     |
| the Global  |                |               | time but     |                                                          |
| Location    |                |               | with minimal |                                                          |
| Service     |                |               | changes and  |                                                          |
| once the    |                |               | acceptable   |                                                          |
| above is    |                |               | discrepancy  |                                                          |
| done        |                |               | we can move  |                                                          |
|             |                |               | ahead)       |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Monitoring  | 29 May         | DoneGreen     | Make sure    | NHADSPLTL-4642e55da6ef-1840-3475-9293-310ba48d502dSystem |
|             |                |               | that system  | JIRA                                                     |
|             |                |               | metrics are  |                                                          |
|             |                |               | being        |                                                          |
|             |                |               | generated    |                                                          |
|             |                |               | correctly    |                                                          |
|             |                |               | and are      |                                                          |
|             |                |               | properly     |                                                          |
|             |                |               | grouped for  |                                                          |
|             |                |               | easy         |                                                          |
|             |                |               | debugging    |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| CICD        | 1st June       | DONEGreen     |              | NHADSPLTL-4643e55da6ef-1840-3475-9293-310ba48d502dSystem |
| Pipeline    |                |               |              | JIRA                                                     |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Cron job to | 2nd June       | DoneGreen     |              | NHADSPLTL-4640e55da6ef-1840-3475-9293-310ba48d502dSystem |
| update the  |                |               |              | JIRA                                                     |
| Maxmind     | **Revised**:   |               |              |                                                          |
| database in | 3rd June       |               |              |                                                          |
| the Global  |                |               |              |                                                          |
| Location    |                |               |              |                                                          |
| Service     |                |               |              |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Training of | 15 June        | DoneGreen     |              | NHADSPLTL-4640e55da6ef-1840-3475-9293-310ba48d502dSystem |
| IP to       |                |               |              | JIRA                                                     |
| detect      |                |               |              |                                                          |
| confidence  |                |               |              |                                                          |
| score based |                |               |              |                                                          |
| on          |                |               |              |                                                          |
| Improving   |                |               |              |                                                          |
| Location    |                |               |              |                                                          |
| Handling\   |                |               |              |                                                          |
| Outcome:    |                |               |              |                                                          |
| confidence  |                |               |              |                                                          |
| score will  |                |               |              |                                                          |
| be          |                |               |              |                                                          |
| available   |                |               |              |                                                          |
| with each   |                |               |              |                                                          |
| response    |                |               |              |                                                          |
| for         |                |               |              |                                                          |
| location    |                |               |              |                                                          |
| detection   |                |               |              |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Handling    | 18 June        | DoneGreen     |              |                                                          |
| DFP         |                |               |              |                                                          |
| location in |                |               |              |                                                          |
| the Global  |                |               |              |                                                          |
| Location    |                |               |              |                                                          |
| Service     |                |               |              |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Pipeline to | 18th June      | IN            | This is a    | NHADSPLTL-4637e55da6ef-1840-3475-9293-310ba48d502dSystem |
| have a      |                | PROGRESSBlue  | prerequisite | JIRA                                                     |
| central     |                |               | for          |                                                          |
| Cache using |                |               | Autoscale.   |                                                          |
| NFS. We     |                |               |              |                                                          |
| would need  |                |               |              |                                                          |
| to write    |                |               |              |                                                          |
| Script to   |                |               |              |                                                          |
| populate    |                |               |              |                                                          |
| local Cache |                |               |              |                                                          |
| using       |                |               |              |                                                          |
| records in  |                |               |              |                                                          |
| NFS         |                |               |              |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Have VMs on | 18th June      | YET TO        | Handles      | NHADSPLTL-4637e55da6ef-1840-3475-9293-310ba48d502dSystem |
| autoscale   |                | STARTEDYellow | traffic      | JIRA                                                     |
| for Global  |                |               | fluctuations |                                                          |
| location    |                |               | and properly |                                                          |
| Service     |                |               | utilizes     |                                                          |
|             |                |               | resources    |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Support for |                | REJECTEDRed   |              | NHADSPLTL-4639e55da6ef-1840-3475-9293-310ba48d502dSystem |
| the         |                |               |              | JIRA                                                     |
| confidence  |                |               |              |                                                          |
| score for   |                |               |              |                                                          |
| IP-based    |                |               |              |                                                          |
| resolution  |                |               |              |                                                          |
| using       |                |               |              |                                                          |
| Enterprise  |                |               |              |                                                          |
| Database    |                |               |              |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Cell Id     | 9th June /     | DONEGreen     | To improve   | NHADSPLTL-4641e55da6ef-1840-3475-9293-310ba48d502dSystem |
| support in  | 10th June      |               | the coverage | JIRA                                                     |
| Global LS   |                |               | of High      |                                                          |
|             | \+ 1 Day       |               | accuracy     |                                                          |
|             | Buffer         |               | detection    |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Support for | 15-16 June     | DoneGreen     | AdEngine and |                                                          |
| Pincode     |                |               | Daedalus     |                                                          |
|             |                |               | support      |                                                          |
|             |                |               | Pincode      |                                                          |
|             |                |               | targetting   |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Migrate     | 24 June        | DoneGreen     | Migrate and  |                                                          |
| Daedalus    |                |               | test with    |                                                          |
| and         |                |               | AdTech and   |                                                          |
| AdEngine    |                |               | resolve      |                                                          |
|             |                |               | issues if    |                                                          |
|             |                |               | any. This    |                                                          |
|             |                |               | confidence   |                                                          |
|             |                |               | to ask other |                                                          |
|             |                |               | teams to     |                                                          |
|             |                |               | migrate      |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+
| Migrate     | Optimistically | DoneGreen     |              |                                                          |
| Content and | by 27 June     |               |              |                                                          |
| other Teams |                |               |              |                                                          |
+-------------+----------------+---------------+--------------+----------------------------------------------------------+

# New requirements for Version 2

  ------------------------------------------------------------------------------------------------------------ -- --
  **Item**                                                                                                        
  Refactor/rewrite CellId training process                                                                        
  Move away from NFS-backed cache. Meanwhile, we will get feedback on how it is performing in the Production      
  Have support for Genomes Id instead of Pelias Ids                                                               
  Refactor Cell ID Learning to improve accuracy                                                                   
  ------------------------------------------------------------------------------------------------------------ -- --

\
