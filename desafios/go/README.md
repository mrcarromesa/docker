# DESAFIO 01 - Docker container golang

* Referência: [Build Small Golang Docker Containers](https://sysadmins.co.za/build-small-golang-docker-containers/)

## Imagem normal

* Execute o comando:

```shell
docker build -t myuser/golang-hello-world .  
```

* Verificar o tamanho da imagem:

```shell
docker images "myuser/golang-hello-world"  
```

* Verificar a coluna `SIZE`

* Executar o container para exibir a mensagem "Code.education Rocks!" executar o comando:

```shell
docker run -it --rm --name hello-world-go carromesa/golang-hello-world  
```

## Imagem com menos de 2MB

* Execute o comando:

```shell
docker build -t myuser/golang-hello-world -f Dockerfile.prod .  
```

* Verificar o tamanho da imagem:

```shell
docker images "myuser/golang-hello-world"  
```

* Verificar a coluna `SIZE`

* Executar o container para exibir a mensagem "Code.education Rocks!" executar o comando:

```shell
docker run -it --rm --name hello-world-go carromesa/golang-hello-world  
```