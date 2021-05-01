# Dockerfile

- Eu tenho uma imagem nginx rodando porém eu preciso ter o vim instalado por exemplo, e eu já queria que ele já estivesse instalado quando eu executar a imagem, e não eu ter que executar a imagem e instalar manualmente.

- A ideia é sempre partir de uma imagem.

- Eu sempre crio uma imagem a partir de uma imagem existente, exemplo:

```
FROM nginx:latest
```

- Depois eu posso rodar comandos normalmente, para executar um comando utilizo o `RUN instrucao_do_comando`
- Importante criar sua propria conta no dockerhub
- Por fim eu executo no terminal o comando:

```shell
docker build -t NOME_DO_MEU_USUARIO_NO_DOCKER_HUB/O_NOME_DA_MINHA_IMAGEM:latest PATH_DA_PASTA_ONDE_ESTA_O_Dockerfile
```

- Ex.:

```shell
docker build -t meuusuario/nginx-com-vim:latest .
```

- o `-t` é o nome da minha imagem ou seja a tag que eu vou definir

- Depois eu posso executar:

```shell
docker ps -a
```

- A minha nova imagem estará lá

- E para acessar posso executar o comando:

```shell
docker run -it NOME_QUE_UTILIZEI_PARA_CRIAR_MINHA_IMAGEM bash
```

- E pronto!

---

# Criar um diretorio e trabalhar dentro dele

- Conteudo em /example2/Dockerfile

- Para criar um diretorio no container e executar comandos dentro dele utilizamos o comando:

```
WORKDIR /NOME_DIR
```

- Comando RUN, para não precisar adicionar vários e vários comandos RUN podemos utilizar o && exemplo:

```
RUN apt-get update && apt-get install PACKAGE -y
```

- Para quebrar linha de um comando utilizamos o `\`:

```
RUN apt-get update && \
    apt-get install PACKAGE -y
```

---

- Para copiar um diretorio da minha máquina para o container utilizamos o comando:

```
COPY NOME_DA_MINHA_PASTA_ATUAL /path/dentro/do/container/
```

- e por fim executo o comando para realizar o build:

```shell
docker build -t meuusuario/nginx-com-vim:latest .
```

---

## Comando fixo e variavel no Dockerfile

```Dockerfile
FROM ubuntu:latest

# Comando fixo
ENTRYPOINT ["echo", "Hello "]

# Comando variavel
CMD ["World"]
```

- a dar um build nesse docker:

```shell
docker build -t meuusuario/hello .
```

- E depois executar:

```shell
docker run --rm meuusuario/hello
```

- Ele irár printar:

```shell
Hello  World
```

- Agora se eu executar o comando:

```shell
docker run --rm meuusuario/hello Mundo
```

- Ele irár printar:

```shell
Hello  Mundo
```

- Isso acontece pois temos o comando fixo:

```Dockerfile
# Comando fixo
ENTRYPOINT ["echo", "Hello "]

```

- O qual sempre irá exibir `Hello `

- E o comando variavel:

```Dockerfile
# Comando variavel
CMD ["World"]
```

- No caso ele irá exibir por padrão `World`, mas substituirá pelo comando que passarmos no final do comando.