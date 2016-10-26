# TCtreaming

TCtreaming is a local video streaming and chatting web based application. It consist of server, client, and streamer.

TCtreaming is build by open broadcaster software or broadcast me, nginx, projekktor, rtmp module.

#### INSTALLATION

###### 1. Video Streaming
--  **Server** --
> Installing nginx with RTMP module
  - installing tools for nginx
  ```sh
$ sudo apt-get install build-essential libpcre3 libpcre3-dev libssl-dev
```
  - Download nginx and RTMP Module
  ```sh
$ wget http://nginx.org/download/nginx-1.9.15.tar.gz
```
```sh
$ wget https://github.com/arut/nginx-rtmp-module/archive/master.zip
```
  - Unpack the downloaded package
```sh
$ tar -zxvf nginx-1.9.15.tar.gz
$ unzip master.zip
$ cd nginx-1.9.15
```
- Build nginx
```sh
$ ./configure --with-http_ssl_module --add-module=../nginx-rtmp-module-master
$ make
$ sudo make install
```
- Nginx installed and start the nginx
```sh
$ sudo /usr/local/nginx/sbin/nginx
```
- Test to make sure nginx is running, text http://<your server ip>/ to your browser and you should get the "Welcome to nginx!" page.

> Configuring nginx to use RTMP

 - Open your config file, located by default at /usr/local/nginx/conf/nginx.conf and add the following at the very end of the file:
```sh
rtmp {
        server {
                listen 1935;
                chunk_size 4096;

                application live {
                        live on;
                        record off;
                }
        }
}
```
 - Restart nginx
```sh
$ sudo /usr/local/nginx/sbin/nginx -s stop
$ sudo /usr/local/nginx/sbin/nginx
```

###### 2. Chatting
--  **Server** --
- Install NodeJs
```sh
$ sudo apt-get update
$ sudo apt-get install nodejs
$ sudo apt install nodejs-legacy
```
- Instalasi NPM
```sh
sudo apt-get install npm
```
- Instalasi nodemon
```sh
sudo npm install -g nodemon
```

#### FILES REQUIREMENT
- Clone or Download [Files Requirement](https://github.com/nawakula/TCtreaming)

#### HOW TO USE TCtreaming FOR SERVER
 - Move the files to /usr/local/nginx/html
 - Edit The IP in the index.html at html directory
 - Start Nginx server - if nginx already started do next stage
 - open TChat directory
 ```sh
cd /usr/local/nginx/html/TChat
```
 - Start NodeJs Server using nodemon
```sh
nodemon index.js
```

#### HOW TO USE TCtreaming FOR STREAMER
- Use Open Broadcaster Software (OBS)
```sh
Streaming Service: Custom
Server: rtmp://<your server ip>/live
Play Path/Stream Key: test
```
 - Use Broadcast Me
 
 Setting the URL 
```sh
rtmp://<your server ip>/live/test/
```
All Done.

