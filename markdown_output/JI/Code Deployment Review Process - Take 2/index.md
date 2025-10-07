## Instructions for this deployment process

This document recommends a code deployment review process for
application and Infrastructure change. The motivation of this process is
to provide a flow that can provide for:

1.  At least one step of a review by someone before deploying into
    production.

2.  A process that can fit well with the existing flow, and tools and
    can be introduced quick without many changes

3.  Code build and deployment should be linked to the ticket system for
    audit purposes and to track the evidence of the deployment pipeline.

### Pre-requisites

[Integration between Jira and
Jenkins](https://support.atlassian.com/jira-cloud-administration/docs/integrate-with-jenkins/)
must be established for linking Jenkins approval in JIRA. The team is
including issue keys (e.g. FUSE-123) in their commit messages (for
deployment information) and branch names (for build information). If
your team isn\'t already doing this, [learn more about referencing
issues in your development
work](https://support.atlassian.com/jira-software-cloud/docs/reference-issues-in-your-development-work/). 

### Process

##### [Manual Deployments]{.underline}

##### [Pipeline Based Deployments]{.underline}

Deployment tracking lets you automatically create or update a change
request from any stage in your Jenkins pipeline.

### Set up deployment tracking using Jenkins CI/CD tool

To set up deployment tracking for your service project using an
alternative CI/CD deployment tool:

1.  From your service project, go to **Project settings \> Change
    management**.

2.  Select **Connect pipeline.**

3.  Select your CI/CD tool to connect Jenkins, then select **Next.**

4.  Select **Create a new service**, then select **Next.**

5.  Enter the **Name,** select the **Tier**, and enter a
    **Description,** then select **Next.**

6.  Select the **Environment type** and **Request type.**

7.  Select **Connect.**

8.  **Copy** the service\'s ID and add this to your deployment
    pipeline's configuration.

### To use deployment tracking with Jenkins:

1.  Go to your Jenkinsfile.

2.  Find the stage in your pipeline where you would like to notify Jira.

3.  Add a **sendJiraDeploymentInfo** block to the stage steps replacing
    your **Jira site name**, **environment ID**, **environment type**,
    and **service ID(s)** you copied from your Jira Service Management
    project.

#### Snippet example

pipeline { agent none stages { stage(\'Build\') { agent any steps { echo
\'Building application\' } } stage(\'Approval\') { agent none options {
timeout(time: 1, unit: \'MINUTES\') } steps { script { def inputValue =
input message: \'Do you want to proceed?\', submitterParameter:
\'USER\', parameters: \[string(defaultValue: \'\', description: \'\',
name: \'Enter your Ldap username\')\] if
(!(\[\'prahlad.ram\'\].contains(inputValue\[\'Enter your Ldap
username\'\]))) { error(\'This user is not approved to deploy.\') }
env.UserApproved = \"\${inputValue\[\'USER\'\]}\" } } }
stage(\'Deployment in development\') { agent any steps {
jiraSendDeploymentInfo ( site: \'evp.atlassian.net\', environmentId:
\'development1\', environmentName: \'development\', environmentType:
\'development\', state: \'successful\', issueKeys: \[ \'TP-14\' \] ) sh
\'echo Deploy to development starting\...\' } } } post { always {
jiraSendBuildInfo site: \'evp.atlassian.net\', branch:
\'TP-14-Jenkins-push\' script { withEnv(\[\'JIRA_SITE=Jira\'\]) {
BUILD_TRIGGER_BY = \"\${currentBuild.getBuildCauses()\[0\].userId}\" def
comment = \[ body: \"\*Build Job\* : \${JOB_NAME}\\n\*Build Number\* :
\${BUILD_NUMBER}\\n\*Build URL\* : \${BUILD_URL}\\n\*Build Status\* :
\${currentBuild.currentResult}\\n\*Build Trigger By\*:
\${BUILD_TRIGGER_BY}\\n\*Approved By\*: \${env.UserApproved}\" \]
jiraAddComment idOrKey: \'TP-14\', auditLog: true, input: comment } } }
} }

#### Sample Pipeline
