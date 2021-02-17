# Integration System Framework

Componentes para a criação das imagens e das configurações necessárias para aplicação Integration System Framework. 
Sendo composto pelos seguintes serviços:

- Mulesoft
- Kong
- Konga
- Elastic Search
- Logstash
- Kibana
- Filebeat
- Jenkins


### Requisitos
* [Docker] - Open platform for developing, shipping, and running applications
* [Docker Compose] - Tool for defining and running multi-container Docker applications.

### Instalação
Iniciar os containers:
```sh
$ docker-compose up -d --build
```
Validar se os containers estão rodando:
```sh
$ docker ps
```

### Configurações necessárias
Os serviços *konga-prepare* e *kong-migration* devem ser iniciados somente a primeira vez, devido a configurações no banco de dados. Após isso os volumes serão compartilhados.

### Configurações
#### Mulesoft
Porta externa disponivel 8081
#### Kong
Kong é o gateway de API de microsserviço de código aberto. Ele está sendo utilizado para proteger, gerenciar e orquestrar APIs de integração criadas no Mulesoft. Para facilitar a configuração do Kong, está sendo utilizada a interface grafica [Konga]. Apos a configuração os serviços vão ser disponibilizados na porta 8000.
#### Logstash
#### Kibana
#### Jenkins


[Docker]: <https://docs.docker.com/get-docker/>
[Docker Compose]: <https://docs.docker.com/compose/>
[Konga]: <http://localhost:1337/>