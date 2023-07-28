# Self-Hosted Sentry 23.4.0

Fork do [Sentry Self-Hosted](https://github.com/getsentry/self-hosted/) com configurações personalizadas para uso do Bridge

## Requisitos

* Docker 19.03.6+
* Compose 2.0.1+
* 4 CPU Cores
* 16 GB RAM
* 200 GB Free Disk Space

## Setup

### Instação e outras configurações

https://develop.sentry.dev/self-hosted/

### Para atualizar

TODO

### Personalizações

- Otimização de uso de memória e armazenamento de logs e usando o RabbitMQ no lugar do Redis para controle de eventos em disco no lugar de usar memória - https://github.com/laboratoriobridge/sentry-self-hosted/commit/c44b45d2c132b0216bf038ff7ba12bcbc544334e
- Limitação de requisições recebidas no Nginx - https://github.com/laboratoriobridge/sentry-self-hosted/commit/8ff91b54aa9cf9564f40f08bb34460918e20cd44
