FROM docker-osx:latest

WORKDIR /main

ENV TOKEN token
ENV URL url
ENV NAME name

EXPOSE 80
EXPOSE 443

RUN apt-get update \
    && apt-get install -y curl
RUN useradd -u 1001 not_root

CMD mkdir actions-runner && cd actions-runner && \
    curl -o actions-runner-osx-arm64-2.313.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.313.0/actions-runner-osx-arm64-2.313.0.tar.gz && \
    # echo "65dd2618b5afa5ae1394388b215da0b763d791b480ae09f0ead956e8f8864c83  actions-runner-osx-x64-2.313.0.tar.gz" | shasum -a 256 -c# Extract the installer
    tar xzf ./actions-runner-osx-arm64-2.313.0.tar.gz && \
    su -c './config.sh --name $NAME --unattended --url $URL --token $TOKEN' not_root && \
    su -c '.run.sh' not_root