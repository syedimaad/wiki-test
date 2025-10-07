  ----------------------- -----------------------
  **Document Status**     Ready-For-ReviewGreen
  **Product Managers**    
  **Product Designers**   
  ----------------------- -----------------------

### [Standard coach]{style="color: rgb(54,179,126);"}[ ]{style="color: rgb(255,86,48);"}[mark duration for DH]{style="color: rgb(54,179,126);"}

  --------------------- --------------------------------------------------------------
  **Coachmarks**        **Standard Duration for DH**
  Toast                 5 secs
  Snackbar              5 secs
  Snackbar with CTA     8 secs
  In-app Notification   8 secs
  Tooltip               5, 8 secs (Unless specified in spec, default will be 5 secs)
  --------------------- --------------------------------------------------------------

### Active and New Xpresso nudges

#### Sheet link: [https://docs.google.com/spreadsheets/d/1oWekxLVt5pHrteSJ4E4kiE1XWcdG5sjEnXTXgLYStJM/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1oWekxLVt5pHrteSJ4E4kiE1XWcdG5sjEnXTXgLYStJM/edit?usp=sharing){card-appearance="inline"}

<table data-layout="wide"
ac:local-id="e88d7156-d9a1-41ce-90ec-fb88047dc616">
<tbody>
<tr>
<td><p>Default home</p></td>
<td><p>Coachmark type</p></td>
<td><p>Description</p></td>
<td><p><strong>Launches (minNumberOfOccurences)</strong></p>
<p><strong><span style="color: rgb(255,86,48);">Should be configurable
at BE</span></strong></p></td>
<td><p>IOS- OS controlled #launch</p></td>
<td><p>Frequency</p></td>
<td><p>Comment</p></td>
<td><p>Should be shown in expresso feed?</p>
<p><strong><span style="color: rgb(255,86,48);">Should be configurable
at BE</span></strong></p></td>
<td><p>Time duration for nudge to be shown</p></td>
<td><p>Conflicts</p></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Select your language</p></td>
<td><p>1</p></td>
<td></td>
<td><p>1</p></td>
<td></td>
<td><p>Not applicable</p></td>
<td><p>Not applicable</p></td>
<td><p>Explore Expresso Nudge (For Thin-LR only)</p>
<p><span style="color: rgb(255,86,48);">Note: </span>not a direct
conflict as language is a feed card.</p></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Feed language selection card</p></td>
<td><p>-1st LR launch(expresso/non-expresso)</p>
<p>-2nd &amp; 1st(ios)</p>
<p><span style="color: rgb(255,86,48);">-5th(to be verified
)</span></p></td>
<td></td>
<td><p>2 (ios)</p>
<p>1(android)</p></td>
<td></td>
<td><p>Not applicable</p></td>
<td><p>Not applicable</p></td>
<td><p>Explore Expresso Nudge (For Thin-LR only)</p>
<p><span style="color: rgb(255,86,48);">Note: </span>not a direct
conflict as language is a feed card.</p></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Expresso Walkthrough coachmark</p></td>
<td><p>1st Expresso launch (expresso/ non-expresso users)</p>
<p><span style="color: rgb(255,86,48);">Phase X: If there a coachmark n
nudge defined for same launch, how we solve for this?</span></p></td>
<td></td>
<td><p>1</p></td>
<td></td>
<td><p>Yes</p></td>
<td><p>Not applicable</p></td>
<td><p>Explore Expresso Nudge (Thin-LR)</p>
<p><span style="color: rgb(255,86,48);">Note: </span>not a direct
conflict as expresso walkthrough will only once user lands on expresso
for first time</p></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Expresso: swipe up</p></td>
<td><p>When user goes to last card of 1st expresso story, user takes no
action till secs, this nudge will come</p>
<p><span style="color: rgb(255,86,48);">phase 2: </span></p>
<p><span style="color: rgb(255,86,48);">(cooling off period)</span></p>
<p>+ less than auto-scroll time</p></td>
<td></td>
<td></td>
<td></td>
<td><p>Yes</p></td>
<td><p>No change</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td><p>Expresso</p></td>
<td><p>Tool tip</p></td>
<td><p>Explore LR</p></td>
<td><p>5th(For all expresso home users)</p></td>
<td></td>
<td></td>
<td></td>
<td><p>Yes</p></td>
<td><p>8 secs</p></td>
<td></td>
</tr>
<tr>
<td><p>LR</p></td>
<td><p>Tool tip</p></td>
<td><p>Expresso discovery nudge (sparkling nudge)</p></td>
<td><p>1st(For Thin-LR, Heavy users)</p>
<p>2nd(For New-Preburn, organic-LR users)</p>
<p>5th(For New-deferred users)</p></td>
<td></td>
<td><p>1</p></td>
<td></td>
<td><p>No</p></td>
<td><p>8 secs</p></td>
<td></td>
</tr>
<tr>
<td><p>Expresso</p></td>
<td><p>In-app notification-like nudge</p></td>
<td><p>In app LR discovery</p></td>
<td><p>8th</p>
<p>(all the expresso home users)</p>
<p>Current implementation(25.0.37): Display this nudge only if user
hasn't viewed LR zone between 1st and xth launch)</p></td>
<td></td>
<td></td>
<td></td>
<td><p>Yes</p></td>
<td><p>8 secs</p></td>
<td></td>
</tr>
<tr>
<td><p>LR</p></td>
<td><p>In-app notification-like nudge</p></td>
<td><p>Expresso discovery nudge</p></td>
<td><p>3rd(Thin-LR)</p>
<p>4th(New-Preburn, organic-LR)</p>
<p>5th(Heavy)</p>
<p>Current implementation(25.0.37): Display this nudge only if user
hasn't viewed Expresso between 1st and xth launch)</p>
<p><span style="color: rgb(255,86,48);">Proposed: Even if the user has
viewed the expresso zone, we will show this nudge.</span></p></td>
<td></td>
<td></td>
<td></td>
<td><p>No</p></td>
<td><p>8 secs</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td><p>Tool tip</p></td>
<td><p>profile walkthrough</p></td>
<td><p>First vist to FPV</p></td>
<td></td>
<td><p>1</p></td>
<td></td>
<td><p>Not applicable</p></td>
<td><p>No change</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Astro: dob &amp; gender selection</p></td>
<td><p>6 / 7(if dismissed/closed)</p></td>
<td></td>
<td><p>2</p></td>
<td><p>2 is hardcoded at client</p>
<p><span style="color: rgb(255,86,48);">Proposed: BE
configurable</span></p></td>
<td><p>No</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>storage, location permission. Single event, prompts for storage
and location separately</p></td>
<td><p>4 / 11/ 18</p>
<p><strong><span style="color: rgb(255,86,48);">Note: Getting every 5th
launch starting from 4th</span></strong></p>
<p><strong><span
style="color: rgb(255,86,48);">4th/9th/14th/19th……</span></strong>.<br />
</p></td>
<td><p>1 only</p></td>
<td><p>first on 4th launch then on 11,18,..</p></td>
<td></td>
<td><p>No</p></td>
<td><p>Not applicable</p></td>
<td><p>Expresso discovery in-app like nudge(new organic-LR, pre-burn
users)</p>
<p><span style="color: rgb(255,86,48);">Proposed: Show location prompt
after the above nudge disappears </span></p></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>battery optimization</p></td>
<td><p>3 (Or once user goes to the notification inbox)</p>
<p><span style="color: rgb(255,86,48);">Note: Not working i.e not
getting in 3rd launch</span></p>
<p><strong><span style="color: rgb(255,86,48);">Getting in 10th
launch</span></strong></p></td>
<td></td>
<td><p>1</p></td>
<td></td>
<td><p>Yes</p></td>
<td><p>Not applicable</p></td>
<td><p>Expresso discovery in-app like nudge(thin users)</p></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>google data policy new version: Your data is safe with
us</p></td>
<td><p>9</p>
<p><span style="color: rgb(255,86,48);">Note: Not working i.e not
getting in 9th launch</span></p>
<p><strong><span style="color: rgb(255,86,48);">Getting in 11th
launch</span></strong></p></td>
<td></td>
<td><p>1</p></td>
<td><p>frequency can be controlled using gapCount</p></td>
<td><p>Yes</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td><p>Expresso</p></td>
<td><p>Change Default-home prompt</p></td>
<td><p>Change_default_home_LR (dialog box)</p></td>
<td><p>15 days from the day of install</p>
<p>Note: Confirmation toast will be shown to users if user changes his
default home</p></td>
<td></td>
<td></td>
<td></td>
<td><p>Yes</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td><p>LR</p></td>
<td><p>Change Default-home prompt</p></td>
<td><p>Change_default_home_expresso (dialog box)</p></td>
<td><p>15 days from the day of install</p>
<p>Note: Confirmation toast will be shown to users if user changes his
default home</p></td>
<td></td>
<td></td>
<td></td>
<td><p>No</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td><p><del>LR</del></p></td>
<td><p><del>Change Default-home toast</del></p></td>
<td><p><del>LR_Changed_home_confirmation</del></p></td>
<td><p><del>After user has clicked yes on Change_default_home_LR (dialog
box)</del></p></td>
<td></td>
<td></td>
<td></td>
<td><p><del>No</del></p></td>
<td><p><del>8 secs</del></p></td>
<td></td>
</tr>
<tr>
<td><p><del>Expresso</del></p></td>
<td><p><del>Change Default-home toast</del></p></td>
<td><p><del>Expresso_Changed_home_confirmation</del></p></td>
<td><p><del>After user has clicked yes on Change_default_home_Expresso
(pop up/dialog box)</del></p></td>
<td></td>
<td></td>
<td></td>
<td><p><del>Yes</del></p></td>
<td><p><del>8 secs</del></p></td>
<td></td>
</tr>
<tr>
<td><p>Expresso/ LR</p></td>
<td></td>
<td><p>Language_change_intimation (Pop up)</p></td>
<td><p>When user deselects expresso language from language
settings</p></td>
<td></td>
<td></td>
<td></td>
<td><p>Not applicable</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>upgrade/linkedin_share</p>
<p>Desc: Prompt to make linkedin the default sharing app</p>
<p>When: prompt is shown only after user shares an item and return to
app</p></td>
<td></td>
<td></td>
<td></td>
<td><p>Eligibilty for prompt to appear:</p>
<p>A. For English users who have Linkedin App Installed</p>
<p>B.min_days_for_upgrade_users = 7, min_days_for_new_users = 30,
repeatAfterDays = 30,60,90,30……</p></td>
<td><p>Not applicable</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>coachmarks for swiping video : Show this nudge when user enters
video immersive/detail for the first time</p></td>
<td><p>First video open</p></td>
<td></td>
<td><p>1</p></td>
<td><p>Proposed:</p>
<p><span style="color: rgb(255,86,48);">a. Change the coachmark
design</span></p>
<p><span style="color: rgb(255,86,48);">b. Wait for some “x” sec for
coacmark to appear</span></p></td>
<td><p>Not applicable</p></td>
<td><p>No change</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Open Create post first time</p></td>
<td><p>First create post open</p></td>
<td></td>
<td><p>1</p></td>
<td><p>Proposed:</p>
<p><span style="color: rgb(255,86,48);">a. Change the coachmark
design</span></p></td>
<td><p>Not applicable</p></td>
<td><p>Not applicable</p></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td><p>Manage Tabs - Open explore first time</p></td>
<td><p>First open to Explore</p></td>
<td></td>
<td><p>1</p></td>
<td></td>
<td><p>Not applicable</p></td>
<td><p>No change</p></td>
<td></td>
</tr>
</tbody>
</table>

### Battery Optimization

\" **Disable Battery Optimization** \"\
\"For you to receive Dailyhunt notifications properly :\
App info \> battery \> Don\'t optimize/ No Restrictions \"

### New nudges configs(Expresso/LR discovery)

### Competitive Analysis- Education & Nudges

- Sharechar

- Google news

- Dainik Jagran

- Inshorts

- ET

- 

1.  Sharechat

+---------------+--------------------+--------------------+-----------+
| **Launch**    | **Prompt type**    | **Frequency**      | **Image** |
+---------------+--------------------+--------------------+-----------+
| 1             | Language           | 1.a . one time     |           |
|               | Onboarding screen  |                    |           |
+---------------+--------------------+--------------------+-----------+
| 1.b           | 1.b. Prompt        | 1.b. one time      |           |
|               | explaining why     |                    |           |
|               | location           |                    |           |
|               | permission is      |                    |           |
|               | needed             |                    |           |
+---------------+--------------------+--------------------+-----------+
| 1.c           | . Location prompt  | Once denied then   |           |
|               |                    | its action driven  |           |
|               |                    | i.e comes only if  |           |
|               |                    | user is trying to  |           |
|               |                    | tag location is    |           |
|               |                    | any prompt2        |           |
+---------------+--------------------+--------------------+-----------+
| 2             | Personalisation    | appears in         |           |
|               | prompt             | consecutive first  |           |
|               |                    | 5 launch           |           |
+---------------+--------------------+--------------------+-----------+
| 3             | Login prompt       |                    |           |
+---------------+--------------------+--------------------+-----------+
| Action driven | 1.  GAllery access | 1.  Clcik on       |           |
|               |                    |     create post    |           |
|               | 2.  Social         |     option         |           |
|               |                    |                    |           |
|               | 3.  Location       | 2.  Click on       |           |
|               |                    |     discover       |           |
|               |                    |     option         |           |
|               |                    |                    |           |
|               |                    | 3.  Create without |           |
|               |                    |     background     |           |
|               |                    |     option in      |           |
|               |                    |     "create post"  |           |
+---------------+--------------------+--------------------+-----------+

2\. Google News

+---------------+--------------------+--------------------+-----------+
| **Launch**    | **Prompt type**    | **Frequency**      | **Image** |
+---------------+--------------------+--------------------+-----------+
| 1st           | Sign-in prompt     | remain in for you  |           |
|               |                    | tab, till the user |           |
|               |                    | sign in            |           |
|               |                    |                    |           |
|               |                    | For-you starts to  |           |
|               |                    | populate once the  |           |
|               |                    | user sign-in       |           |
+---------------+--------------------+--------------------+-----------+
| Action driven | Personalisation    | When user clicks   |           |
|               | prompt             | on follow sources  |           |
|               |                    | in star section    |           |
+---------------+--------------------+--------------------+-----------+
| Action driven | Location prompt    | When user clicks   |           |
|               |                    | on follow location |           |
|               |                    | in star section    |           |
+---------------+--------------------+--------------------+-----------+
| Action driven | Location prompt    | When user clicks   |           |
|               |                    | on follow topics   |           |
|               |                    | in star section    |           |
+---------------+--------------------+--------------------+-----------+

3\. Dainik Jagran

  --------------- ----------------------------- ------------------------------------ -----------
  **Launch**      **Prompt type**               **Frequency**                        **Image**
  1               Language Onboarding screen    1.a . one time                       
  Action driven   When user clicks on profile   Comes everytime till user sign-ins   
  --------------- ----------------------------- ------------------------------------ -----------

4\. Inshorts

+------------+-----------------------+----------------------+-----------+
| **Launch** | **Prompt type**       | **Frequency**        | **Image** |
+------------+-----------------------+----------------------+-----------+
| 1.a        | Language Onboarding   | 1.a . one time       |           |
|            | screen                |                      |           |
+------------+-----------------------+----------------------+-----------+
| 1.b        | Navigation education  | One-time             |           |
|            | prompt                |                      |           |
+------------+-----------------------+----------------------+-----------+
| 1.c        | Personalisation/topic | - One-time           |           |
|            | selection             |                      |           |
|            |                       | - has skip option    |           |
+------------+-----------------------+----------------------+-----------+
| 1.d        | Navigation education  | One-time             |           |
|            | prmopt                |                      |           |
|            |                       |                      |           |
|            | When a user goes to   |                      |           |
|            | the 2nd story on any  |                      |           |
|            | launch                |                      |           |
+------------+-----------------------+----------------------+-----------+
| 2nd launch | Persomalisation       | one-time             |           |
|            | prmopt                |                      |           |
+------------+-----------------------+----------------------+-----------+
| 1st        | Education prompt      | One-time             |           |
+------------+-----------------------+----------------------+-----------+
|            |                       |                      |           |
+------------+-----------------------+----------------------+-----------+

5\. Economic times

  ------------
  **Launch**
  1st
  ------------
