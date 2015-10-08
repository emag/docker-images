# Dockerfile for Sample Rails Application

FROM enakai00/fedora:21
MAINTAINER Etsuji Nakai

# proxy settings
#ENV http_proxy http://example.com:8000
#ENV https_proxy http://example.com:8000

# yum settings
RUN echo "prefer=ftp.riken.jp" >> /etc/yum/pluginconf.d/fastestmirror.conf
RUN yum clean plugins

RUN yum update -y
RUN yum clean all

RUN yum install -y make gcc gcc-c++ ruby-devel rubygem-rails \
                   rubygem-therubyracer libsqlite3x-devel
ADD create_app.sh /usr/local/bin/create_app.sh
RUN chmod u+x /usr/local/bin/create_app.sh && /usr/local/bin/create_app.sh
ADD init.sh /usr/local/bin/init.sh
RUN chmod u+x /usr/local/bin/init.sh
CMD ["/usr/local/bin/init.sh"]