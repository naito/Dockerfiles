# Installs E-Cell3 with IPython
# Another Docker container should build from this one to get services like the notebook

FROM ipython/ipython

MAINTAINER Yasuhiro Naito <ynaito@e-cell.org>

# dependencies
RUN apt-get install -y -q autoconf libtool automake make gcc g++ zlib1g-dev git
RUN apt-get install -y -q python python-dev python-numpy python-pip python-ply
# RUN apt-get install -y -q python-gtk2 python-gnome2
RUN apt-get install -y -q libboost-random-dev libboost-python-dev gsl-bin libgsl0-dev

# install LibSBML
RUN apt-get install -y -q bzip2 libbz2-dev libxml++2.6-dev
RUN pip install python-libsbml

RUN cd /tmp; git clone git://github.com/ecell/ecell3
RUN cd /tmp/ecell3; sh autogen.sh && ./configure --disable-gui && make && make install

VOLUME /ecell3
WORKDIR /ecell3
