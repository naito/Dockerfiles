 # Installs E-Cell3 on miniconda

# FROM continuumio/miniconda
FROM ubuntu:16.04

MAINTAINER Yasuhiro Naito <ynaito@sfc.keio.ac.jp>
LABEL version="0.1"

# GitHub ContinuumIO/docker-images/miniconda/debian/Dockerfile
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing
RUN apt-get install -y wget bzip2 ca-certificates libglib2.0-0 libxext6 libsm6 libxrender1 git mercurial subversion
RUN apt-get clean

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda2-4.3.21-Linux-x86_64.sh -O ~/miniconda.sh
RUN /bin/bash ~/miniconda.sh -b -p /opt/conda
RUN rm ~/miniconda.sh
RUN ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh
RUN echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc
RUN echo "conda activate base" >> ~/.bashrc
RUN find /opt/conda/ -follow -type f -name '*.a' -delete
RUN find /opt/conda/ -follow -type f -name '*.js.map' -delete
RUN /opt/conda/bin/conda clean -ay

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get install -y -q build-essential make gcc g++ zlib1g-dev git

RUN conda install matplotlib notebook
RUN conda install boost gsl ply
RUN conda install autoconf libtool automake
RUN cd /tmp; git clone git://github.com/ecell/ecell3
RUN cd /tmp/ecell3; sh autogen.sh && ./configure --prefix=$CONDA_PREFIX --disable-gui && make && make install

RUN mkdir /notebooks && mkdir /notebooks/BioSim1-00
COPY BioSim1-00/* /notebooks/BioSim1-00/

RUN echo alias ecell3-notebook='"'ecell3-ipython notebook --notebook-dir=/notebooks --ip='*' --port=8888 --no-browser  --allow-root'"' >> ~/.bashrc
CMD [ "/bin/bash" ]
