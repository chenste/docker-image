# DockerFile for tensorflow that supports GUI

FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

RUN apt-get -y update --fix-missing
RUN apt-get -y upgrade

RUN apt-get install tzdata
RUN echo "US/Philadelphia" > /etc/timezone    
RUN dpkg-reconfigure -f noninteractive tzdata

# Install apt-get
RUN apt-get install -y python3-pip python3-dev sudo nautilus feh vim htop ipython3 python3-tk

# Install from pip
RUN pip3 install pyyaml scipy tensorflow-gpu numpy scikit-learn matplotlib

ENV PYTHONPATH "${PYTHONPATH}:/home/developer/Desktop/docker-data/perimeter_defense/pdefense/"

# Replace 1000 with your user / group id
RUN export uid=1009 gid=1009 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer

USER developer
ENV HOME /home/developer/Desktop/docker-data/
WORKDIR /home/developer/Desktop/docker-data/




