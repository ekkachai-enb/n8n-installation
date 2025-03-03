# n8n-installation


## Preparation docker environment
- Please refer to **ec2-install.md** for more information

## Setup docker-compose
- Everything in folder **n8n-docker-compose** will be put to server (EC2)
- **init-data.sh**, this file no need to be updated
- **ssl.cert** and **ssl.key** will be created by SSL certificate provider
- **docker-compose.yml** will be adjusted accordingly to service you want to install
- **.env** is user/password for your Postgres and n8n service