# Requirements
Make sure that you have the following installed:
- [node](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04) 
- npm 
- [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/) and start the mongodb service with `sudo service mongod start`

## Navigate to the Client Folder 
 `cd client`

## Run the folllowing command to install the dependencies 
 `npm install`

## Run the folllowing to start the app
 `npm start`

## Open a new terminal and run the same commands in the backend folder
 `cd ../backend`

 `npm install`

 `npm start`

### Go ahead a nd add a product (note that the price field only takes a numeric input)

## Add a docker file in the backend and frondend

 ## Link mongo do to the app using mongo credentials
 'npm install mongodb' if necesary

 'add mongo connection url'
  mongodb+srv://mongo:<password>@cluster0.kj5ejm.mongodb.net/?retryWrites=true&w=majority

## add a docker compose file to fire up all the services  it should be in the root directory


## File structure should be 
.
├── backend
│   └── Dockerfile
├── client
│   └── Dockerfile
└── docker-compose.yml


## Puhing to dockerhub
RUN 'docker-compose build'
RUN 'docker-compose push'


## To pull the images go to where your compose file is and run 

docker-compose pull
Results 
[+] Running 3/3
 ✔ frontend Pulled                                                         3.6s 
 ✔ mongodb Pulled                                                          2.7s 
 ✔ backend Pulled                                                 

or pull one by one manually from dockerhub (not recomented in this IP)

docker pull jymo/backend-image:v1.0.0
docker pull jymo/frontend-image:v1.0.0
<!-- mongo is not locally built -->
RUN 'docker pull mongo' 

## running Docker compose 
RUN 'docker-compose up' 


Compiled successfully!
yolo-frontend-1  | 
yolo-frontend-1  | You can now view yolo_app in the browser.
yolo-frontend-1  | 
yolo-frontend-1  |   Local:            http://localhost:3000
yolo-frontend-1  |   On Your Network:  http://192.168.112.3:3000
yolo-frontend-1  | 
yolo-frontend-1  | Note that the development build is not optimized.
yolo-frontend-1  | To create a production build, use npm run build.


Access the site via  http://localhost:3000 or On Your Network: in port 3000

Open another terminal
RUN 'docker ps' to view running containers
RUN 'docker container inspect ' to view running containers information ie network, volume etc
RUN 'docker-compose stop' to stop the containers 

  docker-compose stop
[+] Running 3/0
 ✔ Container yolotest-frontend-1  Stopped   0.0s 
 ✔ Container yolotest-backend-1   Stopped   0.0s 
 ✔ Container yolotest-mongodb-1   Stopped

or 'docker-compose down' to remove the running containers

 docker-compose down
[+] Running 4/4
 ✔ Container yolotest-frontend-1  Removed    0.0s 
 ✔ Container yolotest-backend-1   Removed    0.0s 
 ✔ Container yolotest-mongodb-1   Removed    0.0s 
 ✔ Network yolotest_my-network    Removed 



#Git tracking
git log --oneline
d6e5a91 (HEAD -> master, origin/master, origin/HEAD) updated the readme
90e0bf3 modified frontend emage tagging name
010b044 verified Network conectivity between containers and added file structure steps in readme
ea217bb Verified image size and also eddited readme to add steps for docker file in the backend and frondent
653f42e added mongo db description to readme
b79ec71 implemented mongodb connection url in the serves.js to link mongo to my backend successfully
0c9e15a Formated intent and Added comments to explain the docker compose file
00057d7 implemented image versioning in frondent client
bf601ec implemented image versioning in backend
b554e0e implemented bridge custom network to link the containers and their volumes
61e0167 added Docker file in the client app frontend
83ceb3b added Docker file in the Backend app
2fce89b made some instructional changes
9e6eaea added the instructions to run the app for DevOps IP
:...skipping...






###Screenshort of docker hub deployed images link

https://drive.google.com/file/d/1BXDPvSDTIGwB7ElxmhVyjZwiSiY3IGmi/view?usp=drive_link




### ANSIBLE AUTOMATION
add a vagrant vm 
configure vagrant file to specify ansible playbook location
implement ansible tasks using ansible galaxy init
run vagrant provision

## Run the file using  vagrant provision
sudo vagrant provision
==> default: Running provisioner: ansible...
    default: Running ansible-playbook...

PLAY [sample playbook] *********************************************************

TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [ansible-automation : Install 'Docker SDK for Python' using pip] **********
ok: [default]

TASK [ansible-automation : Update pip] *****************************************
changed: [default]

TASK [ansible-automation : Install 'setuptools_rust' package] ******************
changed: [default]

TASK [ansible-automation : Retry installing 'Docker SDK for Python' (docker-compose)] ***
changed: [default]

TASK [ansible-automation : Add Docker official repository] *********************
ok: [default]

TASK [ansible-automation : Install Docker packages] ****************************
ok: [default] => (item=docker-ce)
ok: [default] => (item=docker-ce-cli)
ok: [default] => (item=containerd.io)

TASK [ansible-automation : Start Docker service] *******************************
ok: [default]

TASK [ansible-automation : Add current user to docker group] *******************
ok: [default]

TASK [ansible-automation : Copy Docker Compose file to the VM] *****************
ok: [default]

TASK [ansible-automation : Ensure correct permissions for Docker Compose file] ***
ok: [default]

TASK [ansible-automation : Run Docker Compose pull] ****************************
changed: [default]

TASK [ansible-automation : Run Docker Compose] *********************************
changed: [default]

PLAY RECAP *********************************************************************
default                    : ok=13   changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   






### pulled images in vagrant machine
[vagrant@centos7 YoloApp]$ docker images
REPOSITORY            TAG       IMAGE ID       CREATED       SIZE
mongo                 latest    fb5fba25b25a   2 weeks ago   654MB
jymo/frontend-image   v1.0.0    458f9a8f7545   3 weeks ago   572MB
jymo/backend-image    v1.0.0    4e5ee7bade35   3 weeks ago   191MB

[vagrant@centos7 YoloApp]$ docker ps
CONTAINER ID   IMAGE                       COMMAND                  CREATED          STATUS          PORTS                      NAMES
d5d71607b20a   jymo/backend-image:v1.0.0   "docker-entrypoint.s…"   14 seconds ago   Up 13 seconds   5000/tcp                   nervous_lederberg
2e50da1579d2   mongo:latest                "docker-entrypoint.s…"   2 hours ago      Up 29 minutes   0.0.0.0:27017->27017/tcp   yoloapp-mongodb-1
c7l71sf7b21n   jymo/frontend-image:v1.0.0   "docker-entrypoint.s…"   14 seconds ago   Up 15 seconds   3000/tcp                  frontend-new-1


