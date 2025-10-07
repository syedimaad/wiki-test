1.  Collect all the instance information of a project using command Open
    terminal (if using linux system) or gitbash terminal (if using
    windows)\
    Cmd:   **gcloud auth login** ---\> then enter your email details

**gcloud compute instances list  \--project verse-282813  \>
verse-282813.xls **\

**Replace**  **verse-282813 ---\> project id (example
dh-gcp-ads-prod) **

**   **  **verse-282813.xls → the name of excel sheet you want data
in **

Open google drive upload your excel sheet to get in a proper excel sheet
formate link:
[[https://drive.google.com/]{.underline}](https://drive.google.com/)

       
[https://docs.google.com/spreadsheets/d/1e0lheMbIl-A7B_6sSnhy29sGPKC5re3Z/edit#gid=1454580722](https://docs.google.com/spreadsheets/d/1e0lheMbIl-A7B_6sSnhy29sGPKC5re3Z/edit#gid=1454580722){card-appearance="inline"}
  ---\> this is how the excel sheet looks like 

From the above sheet you will get the total number of vms and total
memory used 

**To find total memory use machine type of the instance**

Example:

E2-**standard-4** --.to this machine_type  RAM = 4x4=16GB

Similarly  if its **highmem-4** RAM =4x8=32GB or **highcpu-4** RAM=
4x1=4GB

For custom type    custom (e2, 12 vCPU, 32.00 GiB) ---\> RAM= 32GB    \
Custom-8-16384 → RAM=16GB

    Custom-8-6384→    RAM=6GB

Using the above details calculate RAM(memory) to all the instance then
add every thing to get       total memory used in a project

**2. To calculate the Total V-CPU\'s**

Go to google console navigate to any project(ads-prod)

Search for **monitoring** in search tab
[[https://console.cloud.google.com/monitoring?project=dh-gcp-ads-prod&timeDomain=1h]{.underline}](https://console.cloud.google.com/monitoring?project=dh-gcp-ads-prod&timeDomain=1h)

Then select **Metrics explorer** located on the left side of the screen 

Then follow the following steps: 

Click on **Select a metric** 

Then select **VM Instances → Instance → Reserved vCPUs → Apply**

Then **Group by** must be project_id and **Aggregator** should be sum

Then value displayed under value column will be total vCPUs ---\-\-\--
in this case its 4.785k

**3. To find total number of disks **

Go to google console navigate to any project(ads-prod)

Search for **Quotas** in search tab
[[https://console.cloud.google.com/iam-admin/quotas?referrer=search&project=dh-gcp-ads-prod&pageState=(%22allQuotasTable%22:(%22f%22:%22%255B%255D%22))]{.underline}](https://console.cloud.google.com/iam-admin/quotas?referrer=search&project=dh-gcp-ads-prod&pageState=(%22allQuotasTable%22:(%22f%22:%22%255B%255D%22)))

In filter search for
[**compute.googleapis.com/disks_total_storage**](http://compute.googleapis.com/disks_total_storage)

**And value in TB under current usage will be Total Disk (TB) for each
project in this case 72.45TB) **

**4. Follow all the above steps to all the projects and update
accordingly.**
