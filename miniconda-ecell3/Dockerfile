# Installs E-Cell3 on miniconda

FROM ubuntu:16.04

MAINTAINER Yasuhiro Naito <ynaito@sfc.keio.ac.jp>
LABEL version="0.2"

# GitHub ContinuumIO/docker-images/miniconda/debian/Dockerfile
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates libglib2.0-0 libxext6 libsm6 libxrender1 git mercurial subversion && \
    apt-get clean

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda2-4.3.21-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    find /opt/conda/ -follow -type f -name '*.a' -delete && \
    find /opt/conda/ -follow -type f -name '*.js.map' -delete && \
    /opt/conda/bin/conda clean -ay

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get install -y -q build-essential make gcc g++ zlib1g-dev git

RUN conda install matplotlib notebook && \
    conda install boost gsl ply && \
    conda install autoconf libtool automake
RUN cd /tmp; git clone git://github.com/naito/ecell3
RUN cd /tmp/ecell3; sh autogen.sh && \
    ./configure --prefix=$CONDA_PREFIX --disable-gui && \
    make && \
    make install

RUN mkdir /notebooks && cd /notebooks \
 && cp -r /tmp/ecell3/samples ./sample_models

RUN echo alias ecell3-notebook='"'ecell3-ipython notebook --notebook-dir=/notebooks --ip='*' --port=8888 --no-browser  --allow-root'"' >> ~/.bashrc
CMD [ "/bin/bash" ]
