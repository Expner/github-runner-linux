FROM ubuntu:22.04

WORKDIR /main

ENV TOKEN token
ENV URL url
ENV NAME name

EXPOSE 80
EXPOSE 443

RUN apt-get update \
    && apt-get install -y curl
RUN useradd -u 1001 not_root