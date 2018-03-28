# DockerFile for tensorflow that supports GUI

FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

RUN apt-get -y update
RUN apt-get -y upgrade

# Install apt-get
RUN apt-get install -y python3-pip python3-dev sudo nautilus feh vim htop ipython3 python3-tk

# Install from pip
RUN pip3 install pyyaml scipy numpy tensorflow-gpu scikit-learn matplotlib pyDOE cvxopt

COPY sobol_seq /tmp/
# DOCKER-VERSION 0.3.4
#bunch of installs
WORKDIR /tmp/
RUN  python3 /tmp/setup.py install 

# Edit bashrc
#RUN echo '#init_tensorflow' >> ~/.bashrc 
#RUN echo 'export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda-8.0/lib64:/usr/local/cuda-8.0/extras/CUPTI/lib64"' >> ~/.bashrc
#RUN echo 'export CUDA_HOME=/usr/local/cuda-8.0/' >> ~/.bashrc
#RUN echo 'export PYTHONPATH=/usr/local/lib/python3.5/dist-packages:$PYTHONPATH' >> ~/.bashrc
#RUN echo 'PATH=${CUDA_HOME}/bin:${PATH}' >> ~/.bashrc
#RUN echo 'export PATH' >> ~/.bashrc

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



