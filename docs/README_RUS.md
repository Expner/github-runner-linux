# kds4wexp/github-actions-linux
___
### Как использовать этот образ
Образ может быть развернут двумя способами:
+ С помощью docker-compose.yml
+ С помощью CLI
___
### Подготовительный этап
+ Зайдите в свой репозиторий GitHub, к которому вы подключаете runner 
+ Settings => Actions => Runner => New self-hosted runner
+ Выберите архитектуру (Linux 64x)
+ Скопируйте токен и url из "Сonfigure"
___
### docker-compose.yml 
Вставьте токен, url и название бегуна в docker-compose.yml.
````
version: "3"
services:
  runner-for-linux:
    image: kds4wexp/github-actions-linux
    environment:
      - TOKEN={ваш_token}
      - URL={ваш_url}
      - NAME={имя_runner}
````
````
$ docker-compose up -d --build 
````
ИЛИ
````
version: "3"
services:
  runner-for-linux:
    image: kds4wexp/github-actions-linux
    environment:
      - TOKEN=your_token
      - URL=your_url
      - NAME=runner_name
````
````
$ docker-compose up -d -e TOKEN={ваш_token} -e URL={ваш_url} -e NAME={имя_runner} --build 
````
___
### CLI
Вставьте токен, url и имя вашего раннера в CLI
````
$ docker run -d --name some-github-runner -e TOKEN={ваш_token} -e URL={ваш_url} -e NAME={имя_runner} kds4wexp/github-actions-linux
````