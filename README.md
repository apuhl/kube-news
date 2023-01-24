# Projeto kube-news

### Objetivo
O projeto Kube-news Ã© uma aplicaÃ§Ã£o escrita em NodeJS e tem como objetivo ser uma aplicaÃ§Ã£o de exemplo pra trabalhar com o uso de containers.

### ConfiguraÃ§Ã£o
Pra configurar a aplicaÃ§Ã£o, Ã© preciso ter um banco de dados Postgre e pra definir o acesso ao banco, configure as variÃ¡veis de ambiente abaixo:

DB_DATABASE => Nome do banco de dados que vai ser usado.

DB_USERNAME => UsuÃ¡rio do banco de dados.

DB_PASSWORD => Senha do usuÃ¡rio do banco de dados.

DB_HOST => EndereÃ§o do banco de dados.

### Criar imagem docker da aplicação

Executar o comando

`docker build -t <account>/<repository>:<tag> -f Dockerfile src/`

onde:

- `account`: seu usuário no Docker Hub
- `repository`: repositório existente ou a ser criado no Docker Hub
- `tag`: tag para versionamento da imagem

Para disponibilizar a imagem no Docker Hub:

- Logar com o comando `docker login`
- Envio da imagem com o comando: `docker push <account>/<repository>:<tag>`

Observação: não esquecer da tag `latest`

### Deploy

Para o deploy, foi criado arquivo manifesto `manifests/deployment.yaml`.

A criação do cluster deve seguir da mesma forma descrita no projeto de [conversão de temperatura](https://github.com/apuhl/conversao-temperatura#deploy-no-k8s)

A criação dos pods deve ser feito utilizando o comando:

`kubectl apply -f manifests/deployment.yaml`

O acesso à página deve ser feito da mesma forma descrita no projeto de [conversão de temperatura](https://github.com/apuhl/conversao-temperatura#testando)