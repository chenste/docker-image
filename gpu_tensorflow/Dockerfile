# DockerFile for tensorflow that supports GUI

FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

RUN apt-get -y update
RUN apt-get -y upgrade

# Install apt-get
# update and install dependencies
RUN         apt-get update \
                && apt-get install -y \
                    software-properties-common \
                    wget \
                && add-apt-repository -y ppa:ubuntu-toolchain-r/test \
                && apt-get update \
                && apt-get install -y \
                    make \
                    git \
                    curl \
                    vim \
                    vim-gnome \
                && apt-get install -y cmake=3.5.1-1ubuntu3 \
                && apt-get install -y \
                    gcc-4.9 g++-4.9 gcc-4.9-base \
                    gcc-4.8 g++-4.8 gcc-4.8-base \
                    gcc-4.7 g++-4.7 gcc-4.7-base \
                    gcc-4.6 g++-4.6 gcc-4.6-base \
                && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.9 100 \
                && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.9 100
RUN apt-get install -y python3-pip python3-dev sudo nautilus feh vim htop ipython3 python3-tk libeigen3-dev

# Install from pip
RUN pip3 install pyyaml scipy numpy tensorflow-gpu scikit-learn matplotlib pyDOE cvxopt

RUN \ 
    pip3 install --no-cache-dir Cython

#RUN pip3 install .


# instal sobol_seq
COPY sobol_seq /tmp/
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



