##  Overview

Identify and discuss team responsibilities by following the instructions
for the [Roles and Responsibilities
Play](https://www.atlassian.com/team-playbook/plays/roles-and-responsibilities).

  ----------------------- -----------------------------------------------------------------------
  **Teams Responsible**   "Two Stake holders from Infra and Two from Dev team for escalations"
  **Team members**        Respective team members ( at-least two primary and fall back from Dev
  **Date**                
  **Brief description**   EX:- Onboard CPU usage high
  ----------------------- -----------------------------------------------------------------------

 

##  Roles and responsibilities

+--------------------+-----------------+-----------------+--------------+
| **Responsibility** | **First level   | **First level   | **Comments** |
|                    | checks from     | checks from     |              |
|                    | Ops**           | Dev**           |              |
+--------------------+-----------------+-----------------+--------------+
| Infra / Ops team   | - Collect CPU   | - This will be  |              |
|                    |   metrics ( top |   filled by Dev |              |
|                    |   command       |   team          |              |
|                    |   output,       |                 |              |
|                    |   number of     | -               |              |
|                    |   connections,  |                 |              |
|                    |   Logs )        |                 |              |
+--------------------+-----------------+-----------------+--------------+
|  Escalation and BU |                 |                 |              |
| stake holder name  |                 |                 |              |
+--------------------+-----------------+-----------------+--------------+
|                    |                 |                 |              |
+--------------------+-----------------+-----------------+--------------+

 

CPU Monitoring URL:-
<http://monitoring.myjosh.in/grafana/d/hb7fSE0Zzasdasdsdqw/system-stats?orgId=5&refresh=30s>

Overall App metrics:-
<http://monitoring.myjosh.in/grafana/d/qwrtffghhsd/onboard-api-stats?orgId=5>

Log URL:-
<https://verse.in.sumologic.com/ui/#/search/0830556d_300b_2634_1983_71db63483d12>

Login/Credentials:- ugc-prod.pem , user root@\<impacted-IP\>

AWS Instance search tag: Onboard

Useful commands:-

top ( Sort by CPU )

\*\* Any other add below
