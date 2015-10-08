# Dockerfile for MySQL Server

FROM enakai00/centos:centos6
MAINTAINER Etsuji Nakai

# proxy settings
#ENV http_proxy http://example.com:8000
#ENV https_proxy http://example.com:8000

# yum settings
RUN echo "prefer=ftp.riken.jp" >> /etc/yum/pluginconf.d/fastestmirror.conf
RUN yum clean plugins

ENV HOME /root
RUN yum -y update
RUN yum -y install mysql-server
RUN yum clean all

ADD init.sh /usr/local/bin/init.sh
RUN chmod u+x /usr/local/bin/init.sh

EXPOSE 3306

CMD ["/usr/local/bin/init.sh"]