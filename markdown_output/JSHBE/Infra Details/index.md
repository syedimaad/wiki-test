The service setup is made using the KEDA in Azure Cloud.

Environment-wise server and storage details for

1.  Build the upload service binary using Golang command

2.  Building Docker Image

3.  Testing by initiating the docker Image

4.  Pushing the generated image to Registry

5.  Apply the manifest file

  ----------------------------- --------------------------- ------------------------------- ------------------------------
  **Environment**               **DEV**                     **QA**                          **PROD**
  Server                        10.74.16.5                  10.73.32.120                    10.70.32.4
  pem file                      josh-onboardpem-azure.pem   josh-qa-azure-transcoding-key   josh-dev-transcoding-key.pem
  Login User                    azureuser                   azureuser                       azureuser
  Registry                      joshdevregistry             joshqaregistry                  joshprodregistry
  Repository                    upload_api                  upload_api                      upload_api
  Tus Storage account           joshdevtuscontent           joshqatuscontent                joshprodtusazcontent
  Tus Container                 tus                         tus                             tus
  Transcoding Storage account   joshdevtranscodingsa        joshqatranscodingsa             joshprodazcontent
  Transcoding Container         josh-dev-content-az         qa-josh-content                 prod-ugc-contents
  ----------------------------- --------------------------- ------------------------------- ------------------------------

Home Directory: /home/azureuser/upload_api

Building the Golang upload service in the server

sh /home/azureuser/upload_api/build_josh_misc_api.sh

Building the docker Image and pushing to the Registry

Command: ./docker_build_image_acr_push.sh  \--registry joshqaregistry
\--repository upload_api \--app-path /home/azureuser/upload_api

Updated manifest file:
 /home/azureuser/upload_api/manifest/upload-api-deployment.yaml

Apply the manifest file

kubectl apply -f
/home/azureuser/upload_api/manifest/upload-api-deployment.yaml

### Docker and Kubectl Commands

- List the images created using the docker command

  - docker images

- Building the docker image

  - docker image build -t
    \${REGISTRY}.azurecr.io/{REPOSITORY}:{currentTime} {APP_PATH}

- Push the docker image

  - docker push {REGISTRY}.azurecr.io/{REPOSITORY}:{currentTime}

- Docker run(initiate image) locally

  - docker run -di -p 8087:8080 -e AWS_ACCESS_KEY_ID=\'{ACCESS_KEY}\' -e
    AWS_SECRET_ACCESS_KEY=\'{SECRET_ACCESS_KEY}\' -e app_env=prod
    \--name=upload_api_1682066402472
    [http://{REGISTRY}.azurecr.io/upload_api:1682066402472](#)

- List docker-initiated processes

  - docker ps -a

- Login to a docker process

  - docker exec -it upload_api_1682064105589 bash

- Get all resources under upload-api namespace

  - kubectl get pods -n upload-api

- Get pod list

  - kubectl get pods -n upload-api

- Deploy manifest file

  - kubectl apply -f
    /home/azureuser/upload_api/manifest/upload-api-deployment.yaml

- Login to an existing Pod

  -  kubectl exec -it upload-api-5589dc6cd4-9gkxm -n upload-api
    /bin/bash
