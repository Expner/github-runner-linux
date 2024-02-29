FROM ubuntu:22.04

WORKDIR /main

ENV TOKEN token
ENV URL url
ENV NAME name

RUN apt-get update \
    && apt-get install -y curl
RUN useradd -u 1001 not_root

CMD mkdir actions-runner && cd actions-runner && \
    curl -o actions-runner-linux-x64-2.313.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.313.0/actions-runner-linux-x64-2.313.0.tar.gz && \
    tar xzf ./actions-runner-linux-x64-2.313.0.tar.gz && \
    ./bin/installdependencies.sh && \
    su -c './config.sh --name $NAME --unattended --url $URL --token $TOKEN' not_root && \
    su -c './run.sh' not_root
