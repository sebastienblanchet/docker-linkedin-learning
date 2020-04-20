# docker build -t name .
# docker run name
# example nanoer
FROM debian:sid
RUN apt-get -y update
RUN apt-get -y install curl
RUN curl https://google.com | wc -c > google-size
ENTRYPOINT echo google this is big; cat google-size
