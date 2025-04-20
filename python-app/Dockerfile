FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y python3.10 python3-pip && \
    ln -sf python3.10 /usr/bin/python3

CMD ["python3", "--version"]
