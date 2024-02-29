# kds4wexp/github-runner-linux64x
___
### Languages
+ [Russian](./docs/README_RUS.md)
___
### DockerHub
+ [DockerHub](https://hub.docker.com/repository/docker/kds4wexp/github-runner-linux64x/general)
___
### How to use this image
The image can be deployed in two ways:
+ via docker-compose.yml
+ via CLI
___
### Preparation step
+ Go to your GitHub repository to which you connect runner 
+ Settings => Actions => Runner => New self-hosted runner
+ Select architecture (Linux 64x)
+ Сopy the token and url from "Сonfigure"
___
### docker-compose.yml 
Paste your token and url and name your runner into docker-compose.yml
````
version: "3"
services:
  runner-for-linux:
    image: kds4wexp/github-runner-linux64x
    environment:
      - TOKEN={your_token}
      - URL={your_url}
      - NAME={runner_name}
````
````
$ docker-compose up -d --build
````
___
### CLI
Paste your token and url and name your runner into CLI
````
$ docker run -d --name some-github-runner -e TOKEN={your_token} -e URL={your_url} -e NAME={runner_name} kds4wexp/github-runner-linux64x
````
