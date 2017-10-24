# DockerFile for tensorflow that supports GUI

FROM ubuntu:16.04

RUN apt-get -y update --fix-missing
RUN apt-get -y upgrade

# Install apt-get
RUN apt-get install -y python3-pip python3-dev sudo nautilus feh vim htop ipython3 python3-tk
RUN apt-get install -y python3-nose
# Install from pip
RUN pip3 install pyyaml scipy numpy scikit-learn matplotlib
RUN pip3 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl 
RUN pip3 install torchvision block qpth

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
ENV HOME /home/developer

