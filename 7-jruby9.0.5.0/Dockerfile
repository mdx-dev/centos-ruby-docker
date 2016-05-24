FROM centos:centos7

MAINTAINER services-engineering@vitals.com

ENV RUBY_DIR /ruby
ENV RUBY_VERSION jruby-9.0.5.0
ENV RUBY_INSTALL $RUBY_DIR/$RUBY_VERSION

RUN rpm -Uvh \
    https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
    yum update -y && \
    yum install -y make which wget tar git \
    gcc gcc-c++ patch readline-devel zlib-devel      \
    libyaml-devel libffi-devel openssl-devel \
    gdbm-devel ncurses-devel libxml-devel bzip2

RUN wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.rpm" && rpm -ivh jdk-8u45-linux-x64.rpm && rm -rf jdk-8u45-linux-x64.rpm

RUN cd /usr/src && \
    git clone https://github.com/sstephenson/ruby-build.git && \
    ./ruby-build/install.sh && \
    mkdir -p $RUBY_INSTALL && \
    /usr/local/bin/ruby-build $RUBY_VERSION $RUBY_INSTALL && \
    rm -rf /usr/src/ruby-build

ENV NODE_VERSION 5.6.0

RUN wget https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.gz -O /tmp/node-v${NODE_VERSION}-linux-x64.tar.gz && \
  tar --strip-components 1 -xzvf /tmp/node-v* -C /usr/local

ENV PATH $RUBY_INSTALL/bin:$PATH
