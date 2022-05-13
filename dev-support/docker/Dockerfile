# start-build-env.sh
# 13/05/2022
# Apache-2.0
# © 2022 – LINAGORA
# @ RLeonard <rleonard@linagora.com>

FROM centos:7

WORKDIR /root

######
# Install common dependencies from packages. Versions here are either
# sufficient or irrelevant.
#
# WARNING: DO NOT PUT JAVA APPS HERE! Otherwise they will install default
# Centos Java.  See Java section below!
######
RUN yum -q update -y &&  yum -q install epel-release -y
#RUN yum -q group install "Development Tools" -y
RUN yum -q install -y centos-release-scl

RUN yum  install -y \
    java-1.8.0-openjdk \
    java-11-openjdk-headless \
    wget

RUN alternatives --set java java-1.8.0-openjdk.x86_64

######
# Install Apache Maven Ant Findbug
######
RUN yum install -y findbugs-bcel ant
ENV MAVEN_HOME /usr
ENV FINDBUGS_HOME /usr

RUN wget https://archive.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
RUN tar xvf apache-maven-3.6.3-bin.tar.gz -C /usr/lib/

RUN yum install -y git

ADD nifi_env_check.sh /root/nifi_env_check.sh
RUN chmod 755 /root/nifi_env_check.sh
RUN echo '~/nifi_env_check.sh' >> /root/.bashrc

