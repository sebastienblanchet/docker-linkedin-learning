# example nanoer
FROM debian:sid
RUN apt-get -y update
RUN apt-get install nano
# run cmd[0] on start with args [1]
CMD ["/bin/nano", "/tmp/notes"]

# in antoher dockerfile
FROM example/nanoer
ADD notes.txt /notes.txt
CMD ["nano", "/notes.txt"]
