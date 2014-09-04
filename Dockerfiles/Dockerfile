# use ubuntu

FROM ubuntu:14.04
MAINTAINER pyanfield <pyanfield@gmail.com>

# install tools
RUN apt-get update -y && apt-get install --no-install-recommends -y -q curl python build-essential git ca-certificates openssh-server

# install golang
RUN mkdir /usr/local/go && curl https://storage.googleapis.com/golang/go1.3.1.linux-amd64.tar.gz | tar xvzf - -C /usr/local/go --strip-components=1

# intall nodejs
# RUN mkdir /nodejs && curl http://nodejs.org/dist/v0.10.29/node-v0.10.29-linux-x64.tar.gz | tar xvzf - -C /nodejs --strip-components=1

# ENV PATH /nodejs/bin:$PATH

# create GOPATH
RUN mkdir -p /home/golang/src
RUN mkdir -p /home/golang/pkg
RUN mkdir -p /home/golang/bin

# set GOPATH
ENV GOPATH /home/golang

ENV PATH /usr/local/go/bin:$PATH

# add a file from your project into the container
# ADD my_projectfiles /path/container_files

# Expose the port
EXPOSE 8080

# for ssh server 
RUN mkdir /var/run/sshd
RUN echo 'root:123456' |chpasswd
EXPOSE 22
CMD    ["/usr/sbin/sshd", "-D"]


# CMD echo hello world