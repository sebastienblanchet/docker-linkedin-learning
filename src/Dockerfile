# docker build -t name .
# docker run name
# example nanoer
FROM debian:sid
RUN apt-get -y update
RUN apt-get -y install curl
RUN curl https://google.com | wc -c > google-size
ENTRYPOINT echo google this is big; cat google-size

# allows for a smaller image size
FROM alpine
COPY --from=builder /google-size /google-size
ENTRYPOINT echo google is this big; cat google-size
