FROM windows:latest

WORKDIR /main

ENV TOKEN token
ENV URL url
ENV NAME name

EXPOSE 80
EXPOSE 443

RUN apt-get update \
    && apt-get install -y curl
RUN useradd -u 1001 not_root

CMD mkdir actions-runner; cd actions-runner && \
    Invoke-WebRequest -Uri https://github.com/actions/runner/releases/download/v2.313.0/actions-runner-win-x64-2.313.0.zip -OutFile actions-runner-win-x64-2.313.0.zip && \
    # if((Get-FileHash -Path actions-runner-win-x64-2.313.0.zip -Algorithm SHA256).Hash.ToUpper() -ne 'c4cb3e5d9f0ab42ddc224cfdf9fb705397a7b20fd321536da5500259225fdf8a'.ToUpper()){ throw 'Computed checksum did not match' }
    Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$PWD/actions-runner-win-x64-2.313.0.zip", "$PWD") && \
    su -c './config.cmd --name $NAME -unattended --url $URL --token $TOKEN' not_root && \
    su -c './run.cmd' not_root