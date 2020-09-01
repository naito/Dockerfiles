# Installs E-Cell3 on miniconda

FROM continuumio/miniconda

MAINTAINER Yasuhiro Naito <ynaito@sfc.keio.ac.jp>

ENV DEBIAN_FRONTEND noninteractive

# Make sure apt is up to date
RUN apt-get update
RUN apt-get upgrade -y

RUN conda install matplotlib notebook
RUN conda install boost gsl ply
RUN conda install autoconf libtool automake
RUN cd /tmp; git clone git://github.com/ecell/ecell3
RUN cd /tmp/ecell3; sh autogen.sh && ./configure --prefix=$CONDA_PREFIX --disable-gui && make && make install

VOLUME /ecell3
WORKDIR /ecell3
