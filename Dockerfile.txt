# Building an image from ubuntu as the base image
FROM ubuntu
MAINTAINER Venkatesh Prasad <venkatesh.prasad@ikea.com>
RUN apt-get upgrade
CMD ["echo" , "Hello World"]
COPY test.txt /tmp
