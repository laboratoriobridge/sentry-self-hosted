# Self-Hosted Sentry 24.10.0

Fork do [Sentry Self-Hosted](https://github.com/getsentry/self-hosted/) com configurações personalizadas para uso do Bridge

## Requisitos

- Docker 19.03.6+
- Compose 2.0.1+
- 4 CPU Cores
- 16 GB RAM
- 200 GB Free Disk Space

## Setup

### Instação e outras configurações

https://develop.sentry.dev/self-hosted/

### Para atualizar

O processo de atualização do Sentry no servidor deve ser feito através da branch master deste repositório. Para isso:

1. Clone este repositório no servidor do Sentry ou localmente.
2. Defina o repositório original como upstream: `git remote add upstream https://github.com/getsentry/self-hosted.git`.
3. Recupere as tags do repositório original: `git fetch --tags upstream`.
4. Atualize as tags no repositório remoto: `git push --tags`.
5. Atualize a branch master com o release para atualização: `git merge [nova_versao]`.

- É importante verificar alterações nos arquivos `config.example` e `conf.example` (existem alguns) e aplicar elas, quando necessário, nos respectivos arquivos conf/config que estão no repositório e no servidor.
- Não devem ser incluídos arquivos vindos de atualizações no diretório `.github`.
- Podem ocorrer conflitos em arquivos de configuração que foram personalizados. A menos que seja proposital, cuidado para não eliminar configurações importantes.

6. Realize `commit` e `push` do merge.
7. Caso não esteja trabalhando no servidor do Sentry, atualize a branch master no servidor.
8. Na pasta raiz do repositório rode a instalação do Sentry: `sudo ./install.sh`. O serviço ficará indisponível por algum tempo.
9. Inicie os containers: `sudo docker compose up -d`

### Personalizações

- Otimização de uso de memória e armazenamento de logs e usando o RabbitMQ no lugar do Redis para controle de eventos em disco no lugar de usar memória - https://github.com/laboratoriobridge/sentry-self-hosted/commit/c44b45d2c132b0216bf038ff7ba12bcbc544334e
  - Alterações no Kafka foram desfeitas - https://github.com/laboratoriobridge/sentry-self-hosted/commit/3300bd6386265433e87d27ad76eb8158ede5f495
- Limitação de requisições recebidas no Nginx - https://github.com/laboratoriobridge/sentry-self-hosted/commit/8ff91b54aa9cf9564f40f08bb34460918e20cd44
- Aumento de tempo de timeout para resposta dos serviços: https://github.com/laboratoriobridge/sentry-self-hosted/commit/6dd8a4e200f211c482fe14885a4209ef8798ce32
