sh

    docker container run hello-world

sh

    docker container ls

sh

    docker container ls -a

sh

    docker container rm ec500950bf77

sh

    docker container rm sweet_mclaren

sh

    docker container run --rm hello-world

sh

    docker container run postgres

 - Imagem pode pegar no dockerhub

sh

    docker container run -e POSTGRES_PASSWORD=newspwd -e POSTGRES_USER=newsuser -e POSTGRES_DB=news postgres

 - variaveis pode pegar no dockerhub

sh

    docker container ls

sh

    docker container exec -it gallant_swirles /bin/bash

sh

 docker container run -e POSTGRES_PASSWORD=newspwd -e POSTGRES_USER=newsuser -e POSTGRES_DB=news -d -p 5432:5432 postgres

 sh

    docker container ls

CONTAINER ID   IMAGE      COMMAND                  CREATED          STATUS          PORTS                                       NAMES
a2afcfbd9290   postgres   "docker-entrypoint.s…"   27 seconds ago   Up 27 seconds   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   xenodochial_payne
efbaa323e4ea   postgres   "docker-entrypoint.s…"   7 minutes ago    Up 7 minutes    5432/tcp                                    gallant_swirles

docker container ls

docker container stop xenodochial_payne

docker container rm -f gallant_swirles

#####################################################################
## Executar um projeto local

clonar https://github.com/jmarcelotse/devops4devs-01

/home/jmarcelotse/tse/devops2.0/devops4devs-01/src

sh

    npm instal

sh

     docker container run -e POSTGRES_PASSWORD=newspwd -e POSTGRES_USER=newsuser -e POSTGRES_DB=news -d -p 5432:5432 postgres

sh

    node server.js

browser

    http://localhost:8080/post

_Essa forma usa localmente utilizando um docker local_

#####################################################################

## Criando uma imagem com dockerfile

Primeiro de tudo é criar o arquivo dockerfile dentro da pasta do projeto.

Verificar se existe uma imagem para o seu projeto no exemplo de conversao temperatura utiliza o NODEJS.

Escrever os manifesto do Dockerfile

/home/jmarcelotse/tse/devops2.0/conversao-temperatura/src

docker build -t conversao-temperatura-v1 -f Dockerfile .

docker image ls

docker image ls -a

docker image prune

docker image rm d2c94e258dcb

docker container run -d -p 8080:8080 conversao-temperatura-v1

FROM
RUN
LABEL
CMD
EXPOSE
ARG
ENV
ADD
COPY
ENTRYPOINT
VOLUME
WORKDIR


docker container rm -f 6d2cf09c0dd7

_Dessa forma o contaneir esta localmente_

#####################################################################

## Criando o container no Docker Register

Caso ja tenha imagem construida usar o docker tag

docker tag conversao-temperatura-v1 jmarcelotse/conversao-temperatura-v1:v1

docker image ls

docker login

docker push jmarcelotse/conversao-temperatura-v1:v1

docker tag  jmarcelotse/conversao-temperatura-v1:v1  jmarcelotse/conversao-temperatura-v1:latest

docker push jmarcelotse/conversao-temperatura-v1

docker build -t jmarcelotse/conversao-temperatura-v1:v1 --push .

docker tag  jmarcelotse/conversao-temperatura-v2:v1  jmarcelotse/conversao-temperatura-v2:latest

docker push jmarcelotse/conversao-temperatura-v2

docker container run -d -p 8080:8080 jmarcelotse/conversao-temperatura-v2:v1