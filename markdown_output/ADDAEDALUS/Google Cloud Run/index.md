## SETUP INSTRUCTIONS

### PROJECT SETUP 

**1. Get project group repository added to Artifact Registry**

Check with the team lead if a new project should use any existing
Artifact registry

> Create a Jira with repository name\
> You will receive the Repository URL in format: \<region-image\>/\<GCP
> Project ID\>/\<Project group\>
>
> **Example:**\
> Jira: IADS-429e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA\
> Response: asia-south1-docker.pkg.dev/dh-gcp-ads-prod/daedalus-projects

**2. Create Instructions file for gitlab:**\
Need to add below files to the project root.

1.  **DockerFile**\
    Contains image creation instructions

    - Please refer to docker documentation for creating the dockerfile.

    - We can use docker-compose as well and update commands in below
      files accordingly\

2.  **.gitlab-ci.yml**\
    Contains instructions for gitlab to process updates to repository\
    *A combined file has been added to Appendix, which can be directly
    used in projects.*\

    1.  Define Image to be used

        yamlimage: docker:latest

    2.  Define stages of deployment \[Can be used to add test stages\]

        yamlstages: - AutoDeploy_non_prod - AutoDeploy_prod - Sandbox -
        Stage - QA - PreProd - Prod

    3.  Define common steps for all stages

        yaml# Default configs extended in all stages defined above, \#
        Will be overridden if same key exists in respective stage
        .default: image: google/cloud-sdk services: - docker:dind
        variables: GCP_PROJECT_ID: script: - echo \$GCP_PROJECT_ID -
        echo \$GCP_SERVICE_KEY \> gcloud-service-key.json \# Google
        Cloud service accounts - gcloud auth activate-service-account
        \--key-file gcloud-service-key.json - gcloud config set project
        \$GCP_PROJECT_ID - gcloud builds submit .
        \--config=cloudbuild.yaml

    4.  Define steps for automatic deployment to Production on push to
        master branch

        yaml# To handle master branch which is named AutoDeploy_prod:
        stage: AutoDeploy_prod only: - master variables: GCP_PROJECT_ID:
        dh-gcp-ads-prod extends: .default before_script: - cp
        .env.production .env

    5.  Other ways of defining the stage steps:

        1.  Define steps for automatic deployment on push to specific
            branch names *\["only" keyword\]*

            yamlAutoDeploy_non_prod: stage: AutoDeploy_non_prod extends:
            .default only: - sandbox - stage - qa - pre-prod variables:
            GCP_PROJECT_ID: dh-gcp-ads-\$CI_COMMIT_REF_NAME
            before_script: - cp .env.\$CI_COMMIT_REF_NAME .env

        2.  Activate a button on gitlab project page to manually deploy
            a branch *\["when:manual"\]*

            yamlStage: stage: Stage extends: .default when: manual
            variables: GCP_PROJECT_ID: dh-gcp-ads-stage before_script: -
            cp .env.stage .env QA: stage: QA extends: .default when:
            manual variables: GCP_PROJECT_ID: dh-gcp-ads-qa
            before_script: - cp .env.qa .env

3.  **cloudbuild.yaml**\
    Contains instructions for cloud platform to deploy the image to
    cloud run\
    **Prerequisites:**

    1.  Artifact registry repository \[ Received from Jira\]

    2.  GCP_PROJECT_ID variable defined in .gitlab-ci.yml

    3.  Project name that should display on cloud run dashboard. This
        name is appended to the Artifact repository url\

        yaml# File: cloudbuild.yaml steps: \# - name:
        \'gcr.io/cloud-builders/docker\' args: \[ \'build\', \'-t\',
        \"asia-south1-docker.pkg.dev/\$PROJECT_ID/daedalus-projects/commerce-revenue\",
        \'.\' , \"\--build-arg\", \"GCP_PROJECT_ID=\$PROJECT_ID\" \] \#
        push the container image - name:
        \'gcr.io/cloud-builders/docker\' args: \[ \'push\',
        \'asia-south1-docker.pkg.dev/\$PROJECT_ID/daedalus-projects/commerce-revenue\'\]
        \# deploy to Cloud Run - name: \"gcr.io/cloud-builders/gcloud\"
        args: \[\'run\', \'deploy\', \'commerce-revenue\', \'\--image\',
        \'asia-south1-docker.pkg.dev/\$PROJECT_ID/daedalus-projects/commerce-revenue\',
        \'\--region\', \'asia-south1\', \'\--platform\', \'managed\'\]

note

And you are done!\
Push these changes to the origin master and navigate to CI/CD Pipeline
on project page to see the deployment logs.\
*(Applicable when automatic deployment with master is configured)*

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
And you are done!\
Push these changes to the origin master and navigate to CI/CD Pipeline
on project page to see the deployment logs.\
*(Applicable when automatic deployment with master is configured)*
:::
::::

------------------------------------------------------------------------

## TROUBLESHOOTING

1.  Deployment Logs

    - Navigate to Project Home \> CI/CD \> Jobs\

2.  Deployment pipeline remains paused.

    - It can happen when a lot of projects are waiting deployment, wait
      for sometime.

    - If no runners are enabled for the project \[refer to Infra
      Setup.B\]\

------------------------------------------------------------------------

## APPENDIX

.gitlab-ci.yml Complete File

This code does the following:

1.  Expose deployment options (to cloud run) on project page of gitlab
    for sandbox, stage, qa, pre-prod

2.  Automatically deploy changes to respective environment if a change
    is pushed to the branch with same name, i.e. any change to branch
    name "sandbox", "stage", "qa", "pre-prod "deploys to stage env.

3.  Automatically deploy any branch change on master to production.

4.  Copy .env.\<environment_name\> file as .env on project root of
    created image

yaml# File: .gitlab-ci.yml image: docker:latest stages: -
AutoDeploy_non_prod - AutoDeploy_prod - Sandbox - Stage - QA - PreProd
\# Default configs extended in stages, can be overridden if same key
exists in respective stage .default: image: google/cloud-sdk services: -
docker:dind variables: GCP_PROJECT_ID: script: - echo \$GCP_PROJECT_ID -
echo \$GCP_SERVICE_KEY \> gcloud-service-key.json \# Google Cloud
service accounts - gcloud auth activate-service-account \--key-file
gcloud-service-key.json - gcloud config set project \$GCP_PROJECT_ID -
gcloud builds submit . \--config=cloudbuild.yaml \# To handle deployment
for non-prod branches AutoDeploy_non_prod: stage: AutoDeploy_non_prod
extends: .default only: - sandbox - stage - qa - pre-prod variables:
GCP_PROJECT_ID: dh-gcp-ads-\$CI_COMMIT_REF_NAME before_script: - cp
.env.\$CI_COMMIT_REF_NAME .env \# To handle master branch which is named
as production AutoDeploy_prod: stage: AutoDeploy_prod only: - master
variables: GCP_PROJECT_ID: dh-gcp-ads-prod extends: .default
before_script: - cp .env.production .env \# For manual deployments
Sandbox: stage: Sandbox extends: .default when: manual variables:
GCP_PROJECT_ID: dh-gcp-ads-sandbox before_script: - cp .env.sandbox .env
Stage: stage: Stage extends: .default when: manual variables:
GCP_PROJECT_ID: dh-gcp-ads-stage before_script: - cp .env.stage .env QA:
stage: QA extends: .default when: manual variables: GCP_PROJECT_ID:
dh-gcp-ads-qa before_script: - cp .env.qa .env PreProd: stage: PreProd
extends: .default when: manual variables: GCP_PROJECT_ID:
dh-gcp-ads-pre-prod before_script: - cp .env.pre-prod .env
