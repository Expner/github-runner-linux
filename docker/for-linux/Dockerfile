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
    #echo "56910d6628b41f99d9a1c5fe9df54981ad5d8c9e42fc14899dcc177e222e71c4  actions-runner-linux-x64-2.313.0.tar.gz" | shasum -a 256 -c && \
    tar xzf ./actions-runner-linux-x64-2.313.0.tar.gz && \
    ./bin/installdependencies.sh && \
    su -c './config.sh --name $NAME --unattended --url $URL --token $TOKEN' not_root && \
    su -c './run.sh' not_root
