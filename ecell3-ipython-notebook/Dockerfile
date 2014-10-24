# Installs E-Cell3 with IPython Notebook
# Another Docker container should build from this one to get services like the notebook

FROM naito/ecell3-ipython

MAINTAINER Yasuhiro Naito <ynaito@e-cell.org>

EXPOSE 8888

# You can mount your own SSL certs as necessary here
ENV PEM_FILE /key.pem
# $PASSWORD will get `unset` within notebook.sh, turned into an IPython style hash
ENV PASSWORD Dont make this your default

ADD notebook.sh /
RUN chmod u+x /notebook.sh

CMD ["/notebook.sh"]
