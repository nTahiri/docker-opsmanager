# MongoDB Ops Manager for docker
- [Intro](#Intro)
  - [Version](#Version)
  - [ChangeLog](Changelog.md)
- [Installation](#Installation)
- [QuickStart](#QuickStart)
- [Configure](#Configure)
  - [Database](#Database)
- [Maintenance](#Maintenance)
- [Referenace](#Referance)

# Intro
  Dockerfile / Docker-compose file to build a MongoDB Ops Manager container image.
## Version
  Currently Version: `1.8.1.290-1`
# Installation
  ```bash
  docker run --name opsmanager -d sahsu/opsmanager
  ```
  and waiting for 3 - 5 mins ( depends on your instance type ) and open http://{YOUR_DOCKER_HOST_IP}:{YOUR_OPSMANAGER_PORT} 
  default port - 8080 and you can add -p 18080:8080 on docker run command for change your port.
# QuickStart
  once you run docker images and waiting for 3 - 5 mins you can open browser to open your ops manager - http://{YOUR_DOCKER_HOST_IP}:{YOUR_OPSMANAGER_PORT}
  for default configure the mongodb for application and backup will running on same instance so you don't need to do anything configure update, for separe Mongodb please check on #Configure
# Configure
  Ops Manager designed to serverless means your app is only app, all data is stored on MongoDB
  By default, if you don't assign **OPSMANAGER_MONGO_APP** then script will create two mongo in local running with port : 27017 & 27018
## Each Env means
  - **OPSMANAGER_CFG**: the main ops manager cfg, you should keep this are same.
  - **OPSMANAGER_BACKUPCFG**: same as **OPSMANAGER_CFG**.
  - **OPSMANAGER_MONGO_APP**: application mongodb URI & Port, default use loaclhost:27017.
  - **OPSMANAGER_CENTRALURL**: default ops manager URI, change it to your FQDN.
  - **OPSMANAGER_CENTRALURLPORT**: default ops manager URI port, change it your port.
  - **OPSMANAGER_BACKUPURL**: default ops manager backup url, should same as **OPSMANAGER_CENTRALURL**.
  - **OPSMANAGER_BACKUPURLPORT**: default ops manager backup url port
  - **OPSMANAGER_FROMEMAIL**: default ops manager from email
  - **OPSMANAGER_ADMINEMAIL**: default ops manager admin email
  - **OPSMANAGER_REPLYTOEMAIL**: default reply email
  - **OPSMANAGER_ADMINFROMEMAIL**: default admin from email
  - **OPSMANAGER_BOUNCEEMAIL**: default bounce email
  - **OPSMANAGER_APPLOG**: default log path
  - **OPSMANAGER_BACKUPLOG**: default backup log path
  - **OPSMANAGER_BACKUPMONGO**: default backup mongo URI ( should same as **OPSMANAGER_MONGO_APP** )
  - **OPSMANAGER_BACKUPPATH**: default backup daemon storage databse path
## Database
  You can use docker-compose.yml to quick start up with app x 1 mongodb x 2 ( for app & backup purpose )
  ``` bash
  cd to docker-opsmanager/
  sudo docker-compose up
  ```
  and you can check on (docker-compose.yml) for more detail information and made your docker-compose configure file.
# Maintenance
  You only upgrade Ops Manager for maintenance but you can easier switch by pull different tag on sahsu/opsmanager ( now default latest = (Version) )
# Referenace
  [Ops Manager newest Manual](https://docs.opsmanager.mongodb.com/current/)
  [Ops Manager Release note](https://docs.opsmanager.mongodb.com/current/release-notes/application/)
  [Ops Manager Download link](https://www.mongodb.com/lp/download/mongodb-enterprise)
