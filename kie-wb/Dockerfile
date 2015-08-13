FROM jboss/base-jdk:8

USER root

# proxy settings
#ENV http_proxy http://proxy.example.com:8080
#ENV https_proxy http://proxy.example.com:8080
#RUN echo "proxy=http://proxy.example.com:8080" >> /etc/yum.conf

# yum settings
RUN echo "prefer=ftp.riken.jp" >> /etc/yum/pluginconf.d/fastestmirror.conf
RUN yum -y update

# kie-wb settings
USER jboss

ENV WILDFLY_VERSION 8.2.1.Final
ENV JBOSS_HOME /opt/jboss/kie-wb
ENV KIE_WB_VERSION 6.2.0.Final

RUN cd $HOME \
    && curl -#LO https://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz \
    && tar xf wildfly-$WILDFLY_VERSION.tar.gz \
    && mv $HOME/wildfly-$WILDFLY_VERSION $JBOSS_HOME \
    && rm wildfly-$WILDFLY_VERSION.tar.gz

RUN curl -#LO "http://search.maven.org/remotecontent?filepath=org/kie/kie-wb-distribution-wars/$KIE_WB_VERSION/kie-wb-distribution-wars-$KIE_WB_VERSION-wildfly8.war"
RUN mv kie-wb-distribution-wars-$KIE_WB_VERSION-wildfly8.war $JBOSS_HOME/standalone/deployments/kie-wb.war
ADD application-users.properties $JBOSS_HOME/standalone/configuration/
ADD application-roles.properties $JBOSS_HOME/standalone/configuration/

EXPOSE 8080

#CMD ["/opt/jboss/kie-wb/bin/standalone.sh", "-b", "0.0.0.0", "-c", "standalone-full.xml", "-Dhttps.proxyHost=proxy.example.com", "-Dhttps.proxyPort=8080"]
CMD ["/opt/jboss/kie-wb/bin/standalone.sh", "-b", "0.0.0.0", "-c", "standalone-full.xml"]
