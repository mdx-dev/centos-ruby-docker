FROM centos:centos7

MAINTAINER services-engineering@vitals.com

ENV RUBY_DIR /ruby
ENV RUBY_VERSION 2.5.0
ENV RUBY_INSTALL $RUBY_DIR/$RUBY_VERSION

RUN rpm -Uvh \
    https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
    yum update -y && \
    yum install -y make which wget tar git \
    gcc patch readline-devel zlib-devel      \
    libyaml-devel libffi-devel openssl-devel \
    gdbm-devel ncurses-devel libxml-devel bzip2

RUN cd /usr/src && \
    git clone https://github.com/sstephenson/ruby-build.git && \
    ./ruby-build/install.sh && \
    mkdir -p $RUBY_INSTALL && \
    /usr/local/bin/ruby-build $RUBY_VERSION $RUBY_INSTALL && \
    rm -rf /usr/src/ruby-build

ENV NODE_VERSION 8.9.4

RUN wget https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.gz -O /tmp/node-v${NODE_VERSION}-linux-x64.tar.gz && \
  tar --strip-components 1 -xzvf /tmp/node-v* -C /usr/local

ENV PATH $RUBY_INSTALL/bin:$PATH
