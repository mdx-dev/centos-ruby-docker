FROM centos:centos7

MAINTAINER Brandon Westcott <brandon.westcott@vitals.com>

ENV RUBY_DIR /ruby/
ENV RUBY_VERSION 2.2.0
ENV RUBY_INSTALL $RUBY_DIR/$RUBY_VERSION

RUN rpm -Uvh \
    https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
    yum update -y && \
    yum install -y make which wget tar git \
    gcc patch readline-devel zlib-devel      \
    libyaml-devel libffi-devel openssl-devel \
    gdbm-devel ncurses-devel libxml-devel

RUN wget http://nodejs.org/dist/v0.12.7/node-v0.12.7-linux-x64.tar.gz -O /tmp/node-v0.12.7-linux-x64.tar.gz && \
  tar --strip-components 1 -xzvf /tmp/node-v* -C /usr/local

RUN mkdir $RUBY_DIR && \
    cd $RUBY_DIR    && \
    git clone https://github.com/sstephenson/ruby-build.git && \
    $RUBY_DIR/ruby-build/install.sh                         && \
    cd $RUBY_DIR/ruby-build && ./bin/ruby-build $RUBY_VERSION $RUBY_INSTALL && \
    rm -rf $RUBY_DIR/ruby-build

ENV PATH $RUBY_INSTALL/bin:$PATH
