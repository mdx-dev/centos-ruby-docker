# CentOS 6 + Ruby 2 Docker Image

Installs Ruby 2 using [`ruby-build`](https://github.com/sstephenson/ruby-build) and includes 
several useful command-line utilities like `which`, `wget`, `tar`, etc. GCC and "typical" 
libraries, left installed for building native Gems.

It's meant to be used with [`docker-compose`]() and contains no `CMD` or `ENTRYPOINT`.

# How to use this image

## Create a `Dockerfile` in your project

    FROM vitals:centos6-ruby2

Put this file in the root of your app, next to your `docker-compose.yml` file.

Build and run the Docker image.
