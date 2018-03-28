# DockerFile for tensorflow that supports GUI

FROM ubuntu:16.04

RUN apt-get -y update --fix-missing
RUN apt-get -y upgrade


# Install apt-get
RUN apt-get install -y python3-pip python3-dev sudo nautilus feh vim htop ipython3 python3-tk

# Install from pip
RUN pip3 install pyyaml scipy numpy tensorflow scikit-learn matplotlib pyDOE cvxopt

COPY sobol_seq /tmp/
# DOCKER-VERSION 0.3.4
#bunch of installs
WORKDIR /tmp/
RUN  python3 /tmp/setup.py install 

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer

USER developer
ENV HOME /home/developer/Desktop/docker-data/
WORKDIR /home/developer/Desktop/docker-data/




