# Projeto kube-news

### Objetivo
O projeto Kube-news é uma aplicação escrita em NodeJS e tem como objetivo ser uma aplicação de exemplo pra trabalhar com o uso de containers.

### Configuração
Pra configurar a aplicação, é preciso ter um banco de dados Postgre e pra definir o acesso ao banco, configure as variáveis de ambiente abaixo:

DB_DATABASE => Nome do banco de dados que vai ser usado.

DB_USERNAME => Usuário do banco de dados.

DB_PASSWORD => Senha do usuário do banco de dados.

DB_HOST => Endereço do banco de dados.

### Criar imagem docker da aplica��o

Executar o comando

`docker build -t <account>/<repository>:<tag> -f Dockerfile src/`

onde:

- `account`: seu usu�rio no Docker Hub
- `repository`: reposit�rio existente ou a ser criado no Docker Hub
- `tag`: tag para versionamento da imagem

Para disponibilizar a imagem no Docker Hub:

- Logar com o comando `docker login`
- Envio da imagem com o comando: `docker push <account>/<repository>:<tag>`

Observa��o: n�o esquecer da tag `latest`

### Deploy

Para o deploy, foi criado arquivo manifesto `manifests/deployment.yaml`.

A cria��o do cluster deve seguir da mesma forma descrita no projeto de [convers�o de temperatura](https://github.com/apuhl/conversao-temperatura#deploy-no-k8s)

A cria��o dos pods deve ser feito utilizando o comando:

`kubectl apply -f manifests/deployment.yaml`

O acesso � p�gina deve ser feito da mesma forma descrita no projeto de [convers�o de temperatura](https://github.com/apuhl/conversao-temperatura#testando)