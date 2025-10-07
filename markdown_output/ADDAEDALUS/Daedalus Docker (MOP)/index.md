## **Procedures**

- **Remove any Docker files that are running in the system**

sudo apt-get remove docker docker-engine
[http://docker.io](http://docker.io){card-appearance="inline"}

- **Check if the system is up-to-date**

sudo apt-get update

- **Install Docker** 

sudo apt install
[http://docker.io](http://docker.io){card-appearance="inline"}

- **Install docker-compose**

sudo apt install docker-compose

- **Permit** ***docker.sock*** **file**

sudo chmod 666 /var/run/docker.sock

- **Before testing Docker, check the version **

docker \--version

- **Clone repository on your machine**

git clone
[[https://gitlab.dailyhunt.in/nh-ads-platform/Daedalus.git]{.underline}](https://gitlab.dailyhunt.in/nh-ads-platform/Daedalus.git)

- **Switch to the docker branch**

git checkout docker-home

- **Start the docker**

sudo docker-compose up

- **Permit specific folders**

sudo chmod -R 777 public/

sudo chmod -R 777 storage/\*

sudo chmod -R 777 bootstrap/

## **Notes**

- If you want to connect a MySQL instance on local machine use `db` as
  the hostname in `.env` file.
