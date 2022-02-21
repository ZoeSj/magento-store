## How to install the magento2 on docker?
This project use Apache 2.4 + (PHP 7.3 + OPCache + XDebug) + MariaDB + Redis + Elasticsearch 6.8 + magento 2.3.4.

For macOS
### step 1 check the version
```
docker -v

here is mine:
Docker version 20.10.5, build 55c4c88

docker-compose -v

here is mine:
docker-compose version 1.29.0, build 07737305
```

### step 2 get the file
```
a mkdir new file name
b go to the file and git clone this project
git@github.com:ZoeSj/magento-store.git <project_folder>
```
### step 3 start build this project
<sup>Script ask you about project name, and link to git repo</sup>
```
bin/init #init the project,and just name the project then enter.
```
### step 4 go to src and get the magento code
Add new file called src on root directory.Put all your project files under ./src directory.
```
cd src
rm -rf index.php
```
```
composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition=2.3.4 ./ --ignore-platform-reqs

cd ..
```
### step 5 start docker
```
docker compose up
bin/copytocontainer --all # Copy all your files from host machine to container by running
bin/permissions
```
### step 6 go to web and install the magento
just care the php ext(sockets),maybe you need to install it on docker apache container.
```
RUN docker-php-ext-install sockets
```