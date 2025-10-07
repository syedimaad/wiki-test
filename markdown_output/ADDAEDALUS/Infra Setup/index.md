### **A. Add GCP Service Account key on Gitlab project**

*Gitlab Project \> Settings \> CI/CD \> Variables*

This configuration has been implemented for all the projects by default.
However, they have been added here for information/troubleshooting

1.  **Check if exists:**\
    The key can exist either under Project or group variables. It has
    been added on both for demo purpose on below screenshot, but having
    it at either one of them will work fine.

2.  **Getting a new one created:**\
    If you dont see any of them, raise a Jira ticket with following
    details:

    - **Subject**: GCP Service key addition for CICD for Google cloud
      Run/Functions

    - **Body**: Link to git project/Project group \[Having a key added
      to project group can enable this for all projects within that
      group, and show up under Group Variables\]

------------------------------------------------------------------------

### **B. Enable Runners for your Project**

*Gitlab Project \> Settings \> CI/CD \> Runners*

1.  Please ensure that shared runners are active for your project like
    below:\
