## SETUP INSTRUCTIONS

\
**1. Enable Runners for your project**\
Refer to Infra Setup, Heading "B"

\
**2. Need to add .gitlab-ci.yml file to the project root with below
code. It will ensure the following:**

1.  Any push to branches named "sandbox", "stage", "qa", "pre-prod"
    shall be deployed to respective environments automatically.

2.  Any push to branch named "master" shall be deployed to production
    automatically.

3.  Expose option on gitlab project pages to deploy any branch to any of
    the environment

4.  Depending upon the project, deployment may take some time. You may
    view its status/logs on gitlab project page \> CI/CD \> Jobs

Please update `<FUNCTION_NAME>` on line 11 and other function
configurations on line 22-26

yamlstages: - AutoDeploy_non_prod - Sandbox - Stage - QA - PreProd -
AutoDeploy_prod variables: FUNCTION_NAME: \<FUNCTION_NAME\>
GCP_PROJECT_ID: none .default: image: google/cloud-sdk script: - echo
\$GCP_PROJECT_ID - echo \$GCP_SERVICE_KEY \> gcloud-service-key.json -
gcloud auth activate-service-account \--key-file
gcloud-service-key.json - gcloud config set project \$GCP_PROJECT_ID -
gcloud functions deploy \$FUNCTION_NAME \--runtime=python39
\--entry-point=\$FUNCTION_NAME \--region=asia-south1 \--source=.
\--trigger-http \# To handle deployment for non-prod branches
AutoDeploy_non_prod: stage: AutoDeploy_non_prod extends: .default
only: - sandbox - stage - qa - pre-prod variables: GCP_PROJECT_ID:
dh-gcp-ads-\$CI_COMMIT_REF_NAME \# To handle master branch which is
named as production AutoDeploy_prod: stage: AutoDeploy_prod only: -
master variables: GCP_PROJECT_ID: dh-gcp-ads-prod extends: .default \#
For manual deployments Sandbox: stage: Sandbox extends: .default when:
manual variables: GCP_PROJECT_ID: dh-gcp-ads-sandbox Stage: stage: Stage
extends: .default when: manual variables: GCP_PROJECT_ID:
dh-gcp-ads-stage QA: stage: QA extends: .default when: manual variables:
GCP_PROJECT_ID: dh-gcp-ads-qa PreProd: stage: PreProd extends: .default
when: manual variables: GCP_PROJECT_ID: dh-gcp-ads-pre-prod note

And you are done!

- All the other setup steps have been pre-configured on GCP and gitlab
  project

- Push these changes to the origin and navigate to CI/CD Pipeline on
  project page to see the deployment logs.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
And you are done!

- All the other setup steps have been pre-configured on GCP and gitlab
  project

- Push these changes to the origin and navigate to CI/CD Pipeline on
  project page to see the deployment logs.
:::
::::

## Troubleshooting

Refer to Troubleshooting section of [CI/CD for Google cloud Run via
gitlab](https://evp.atlassian.net/wiki/pages/resumedraft.action?draftId=122224764)
or steps in Infra Setup
