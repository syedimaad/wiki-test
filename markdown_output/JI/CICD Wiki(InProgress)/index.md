This wiki has high-level information only.

1.  You will have to add the Jenkinsfile to the repository.

    1.  Sample:

        1.  NodeJs:
            <https://gitlab.dailyhunt.in/saurabh.srivastava/josh-cms-api/blob/azure_qa/jenkinsfile>

        2.  Java:
            <https://gitlab.dailyhunt.in/saurabh.srivastava/josh-gateway/blob/master-azure-qa/Jenkinsfile>

2.  You should have already onboarded sonarqube project for the same.

3.  Packer json file should have the next version of the image before
    execution. (Manual step)

4.  The version should also be updated in the wrapper file.

5.  You will have to choose the correct env & based on that, it will
    pick all the correct parameters.

you can have a look at the below job for more information.\
<https://cicd.dailyhunt.in/view/JOSH/job/azure-josh-gateway-ci/job/master-azure-qa/78/console>
