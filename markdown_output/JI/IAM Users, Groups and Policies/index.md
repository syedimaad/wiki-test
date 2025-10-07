## Brief

This document proposes some best practices to configure AWS IAM for
secure and maintainable access management for identities(people,
machines) to AWS resources.

## AWS Identity and Access Management (IAM)

IAM provides authentication and authorisation for the AWS API. When you
send a request to the AWS API, IAM verifies your identity and checks if
you are allowed to perform the action. IAM controls who (authentication)
can do what (authorisation) in the AWS account.

- An *IAM user* is used to authenticate people accessing your AWS
  account.

- An *IAM group* is a collection of IAM users.

- An *IAM role* is used to authenticate AWS resources, for example an
  EC2

- instance.

- An *IAM policy* is used to define the permissions for a user, group,
  or role.

## Users/Identities

Kinds of users/identities who need to access and authorise to AWS
resources

  --------------------------- ----------------------------------------------------------------------------- -----------------------------------------------------------
  **Kind**                    **Example**                                                                   **AWS Resource Interaction**
  People-Internal             Infra, Engineering, Business team members requiring access to AWS resources   AWS Console, AWS APIs, AWS CLI, other client applications
  People-External/Temporary   External consultants(like G7CR) users working on projects                     AWS Console, AWS APIs, AWS CLI, other client applications
  Machines                    EC2 instances, Lambda functions, automation/provisioning accounts             AWS APIs, AWS CLI, other client applications
  --------------------------- ----------------------------------------------------------------------------- -----------------------------------------------------------

## Groups

Example recommendation of groups based on existing teams and job
functions

  ----------------------------------------- -----------------------------------------------------------------
  Team/IAM Group                            Members
  josh-admins                               DevOps, SRE
  josh-infral1                              Infra Interns
  josh-infra-g7cr                           G7CR DevOps
  josh-networks                             Networks
  josh-dba                                  DBA
  josh-billing                              Billing
  josh-engineering-leads                    All Josh Engineering Leads
  josh-api                                  OnBoardAPI Java, OnboardAPI GoLang
  josh-feed                                 FeedEngine,
  josh-gateway                              Gateway
  josh-share                                
  josh-analytics                            
  josh-aiml                                 
  josh-transcode                            
  josh-cms                                  
  josh-notification                         
  josh-joshcam                              
  josh-joshlive                             
  josh-newfeature-temp                      Temporary Group
  josh-infra-provisioning-machineaccounts   Machine Accounts used for Infra Provisioning
  josh-feed-discovery-machineaccounts       Machine Accounts used by Feed application for Discovery feature
  ----------------------------------------- -----------------------------------------------------------------

## Improvement Recommendations

- Use strong sign-in mechanisms by enforcing password policies,
  credential rotation and MFA

- Machine users will not have MFA or short-lived tokens (AWS STS) as of
  now, however their access & secret keys will be frequently rotated.
  **Machine accounts** will belong to **Groups** as well for better
  organisation and association. AWS STS for Machine Accounts will be
  implemented at a later stage

- Enforcing separation of duties with appropriate authorisation of
  identities to **AWS resources** with **IAM policies** authorising
  access based on **tags.** Users performing similar job function will
  be added to **IAM groups** to which **IAM policies** will be attached

- Access and Permissions are granted/assigned following the principle of
  Least Privilege after securing approvals. Addition of members to
  proposed groups, modification of existing policies should follow the
  usual channel access request in JIRA with approvals

- **IAM roles** will be used allow AWS resources and machine identities
  to access other AWS APIs

- Pre-configure AWS roles and policies required for AWS resources such
  that when a resource is setup we don't setup a new set of roles and
  policies for it. For example, pre-configure roles and policies needed
  for AWS Kinesis to work and then initialising this a new Kinesis
  cluster just opt for the existing Kinesis roles and policies.

- Central Identity Management and integration with **Google SSO.** This
  allows creating, managing and revoking from a single location making
  it easier to manage access. This reduces the requirement for multiple
  credentials and provides an opportunity to integrate with HR processes

- AWS resources will come with best practices guide for identities who
  are granted access to it to know the advisable actions to perform on
  those resources.

## Example IAM Policies

+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| **Service**     | **Resource** | **Group**              | **Access     | **Allow Action**             | **Deny   | **Condition**          |
|                 |              |                        | Level**      |                              | Action** |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| EC2             | \*           | josh-engineering-leads | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read,  |                              |          | josh                   |
|                 |              |                        | Tagging      |                              |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| EC2             | \*           | josh-engineering-leads | **Limited:** | ec2:StartInstances\          |          | aws:ResourceTag/bu:    |
|                 |              |                        | Write        | ec2:StopInstances\           |          | josh                   |
|                 |              |                        |              | ec2:RebootInstances\         |          |                        |
|                 |              |                        |              | ec2:CreateSnapshots\         |          |                        |
|                 |              |                        |              | ec2:AttachVolume\            |          |                        |
|                 |              |                        |              | ec2:ModifyInstanceAttribute\ |          |                        |
|                 |              |                        |              | ec2:SentDiagnosticInterrupt\ |          |                        |
|                 |              |                        |              | ec2:DetachVolume\            |          |                        |
|                 |              |                        |              | ec2:RunInstances\            |          |                        |
|                 |              |                        |              | ec2:CreateLaunchTemplate     |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| EC2             | \*           | josh-api               | **Full:**    | \*                           |          | aws:ResourceTag/owner: |
|                 |              |                        | List, Read   |                              |          | api                    |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| EC2             | \*           | josh-api               | **Limited:** | ec2:StartInstances\          |          | aws:ResourceTag/owner: |
|                 |              |                        | Write        | ec2:StopInstances\           |          | api                    |
|                 |              |                        |              | ec2:RebootInstances\         |          |                        |
|                 |              |                        |              | ec2:CreateSnapshots          |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| EC2             | \*           | josh-feed              | **Full:**    | \*                           |          | aws:ResourceTag/owner: |
|                 |              |                        | List, Read   |                              |          | feed                   |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| EC2             | \*           | josh-feed              | **Limited:** | ec2:StartInstances\          |          | aws:ResourceTag/owner: |
|                 |              |                        | Write        | ec2:StopInstances\           |          | feed                   |
|                 |              |                        |              | ec2:RebootInstances\         |          |                        |
|                 |              |                        |              | ec2:CreateSnapshots          |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| Kinesis         | \*           | josh-engineering-leads | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read,  |                              |          | josh                   |
|                 |              |                        | Tagging,     |                              |          |                        |
|                 |              |                        | Write        |                              |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| Kinesis         | \*           | josh-api               | **Full:**    | \*                           |          | aws:ResourceTag/owner: |
|                 |              |                        | List, Read   |                              |          | api                    |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| Kinesis         | \*           | josh-api               | **Full:**    | CreateStream\                |          | aws:ResourceTag/owner: |
|                 |              |                        | Write        | DeleteStream                 |          | api                    |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| ElastiCache     | \*           | josh-engineering-leads | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read   |                              |          | josh                   |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| ElastiCache     | \*           | josh-api               | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read   |                              |          | josh                   |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| CloudWatch      | \*           | josh-engineering-leads | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read   |                              |          | josh                   |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| CloudWatch      | \*           | josh-api               | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read   |                              |          | josh                   |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| KinesisFirehose | \*           | josh-engineering-leads | **Full:**    | \*                           |          | aws:ResourceTag/bu:    |
|                 |              |                        | List, Read,  |                              |          | josh                   |
|                 |              |                        | Tagging,     |                              |          |                        |
|                 |              |                        | Write        |                              |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| KinesisFirehose | \*           | josh-api               | **Full:**    | \*                           |          | aws:ResourceTag/owner: |
|                 |              |                        | List, Read   |                              |          | api                    |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| KinesisFirehose | \*           | josh-api               | **Full:**    | CreateDeliveryStream\        |          | aws:ResourceTag/owner: |
|                 |              |                        | Write        | DeleteDeliveryStream         |          | api                    |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| Lambda          | \*           | josh-engineering-leads | Full         | **Managed Policy:**          |          | \*                     |
|                 |              |                        |              | AWSLambda_FullAccess         |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| Lambda          | \*           | josh-api               | Full         | **Managed Policy:**          |          | Lambda does not allow  |
|                 |              |                        |              | AWSLambda_FullAccess         |          | authorisation via      |
|                 |              |                        |              |                              |          | tags. So we can        |
|                 |              |                        |              |                              |          | conditionally grant    |
|                 |              |                        |              |                              |          | access to lambdas      |
|                 |              |                        |              |                              |          | using ARNs (If         |
|                 |              |                        |              |                              |          | required)              |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| \*              | \*           | josh-admins            |              | **Managed Policy:**\         |          |                        |
|                 |              |                        |              | AdministratorAccess          |          |                        |
|                 |              |                        |              |                              |          |                        |
|                 |              |                        |              | \                            |          |                        |
|                 |              |                        |              | **Custom Policy:**\          |          |                        |
|                 |              |                        |              | MFA_Enforce\                 |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| \*              | \*           | josh-networks          |              | **Managed Policy:**\         |          |                        |
|                 |              |                        |              | NetworkAdministrator\        |          |                        |
|                 |              |                        |              | IAMUserChangePassword        |          |                        |
|                 |              |                        |              |                              |          |                        |
|                 |              |                        |              | **Custom Policy:**\          |          |                        |
|                 |              |                        |              | manage-own-access-key\       |          |                        |
|                 |              |                        |              | MFA_Enforce                  |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| \*              | \*           | josh-dba               |              | **Managed Policy:**\         |          |                        |
|                 |              |                        |              | DatabaseAdministrator\       |          |                        |
|                 |              |                        |              | IAMUserChangePassword        |          |                        |
|                 |              |                        |              |                              |          |                        |
|                 |              |                        |              | **Custom Policy:**\          |          |                        |
|                 |              |                        |              | manage-own-access-key\       |          |                        |
|                 |              |                        |              | MFA_Enforce                  |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+
| \*              | \*           | josh-infral1           |              | **Managed Policy:**\         |          |                        |
|                 |              |                        |              | ReadOnlyAccess\              |          |                        |
|                 |              |                        |              | IAMUserChangePassword\       |          |                        |
|                 |              |                        |              | \                            |          |                        |
|                 |              |                        |              | **Custom Policy:**\          |          |                        |
|                 |              |                        |              | manage-own-access-key\       |          |                        |
|                 |              |                        |              | MFA_Enforce                  |          |                        |
+-----------------+--------------+------------------------+--------------+------------------------------+----------+------------------------+

## Open Action Items

1 incomplete [Tagging AWS resources - In
Progress]{.placeholder-inline-tasks}

2 incomplete [Enabling MFA for human users. - In
Progress]{.placeholder-inline-tasks}

3 incomplete [Password and Credential Rotation Policy
Creation]{.placeholder-inline-tasks}

4 incomplete [IAM Group and Policy SignOff]{.placeholder-inline-tasks}

5 incomplete [Integrating with Google SSO]{.placeholder-inline-tasks}

6 incomplete [Jira template creation for access request with pre-defined
fields to reduce ambiguity and enable quick
action]{.placeholder-inline-tasks}

7 incomplete [Best Practices guide spanning tips for Cost Optimisation,
Security and Reliability for AWS PaaS resources like EMR, Kinesis
]{.placeholder-inline-tasks}
