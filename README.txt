Information on creating docker file that supports GUI

1) http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/
2) https://blog.docker.com/2013/07/docker-desktop-your-desktop-over-ssh-running-inside-of-a-docker-container/

1) Create dockerfile called DockerFile (see example docker file)
2) cd into folder with dockerfile
3) nvidia-docker build -t [NAME OF IMAGE] .
   Ex: 
   nvidia-docker build -t tensorflow .
4) Create a folder that you want to share
5) nvidia-docker run -ti --rm \
       -e DISPLAY=$DISPLAY \
       -v /tmp/.X11-unix:/tmp/.X11-unix \
       -v [PATH OF SHARED FOLDER]:[LOCATION IN DOCKER CONTAINER] \
       [NAME OF IMAGE] bash
   Ex:
   nvidia-docker run -ti --rm \
       -e DISPLAY=$DISPLAY \
       -v /tmp/.X11-unix:/tmp/.X11-unix \
       -v ~/docker-data/:/home/developer/Desktop/docker-data/ \
       tensorflow bash

