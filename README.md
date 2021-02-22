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
Copiar a chave gerada para o primeiro acesso
Acesse o container utilizando o seguinte comando no CMD:
```sh
$ docker exec -it jenkins /bin/bash
```
Execute o seguinte comando nesse mesmo CMD:
```sh
$ cat /var/jenkins_home/secrets/initialAdminPassword
```
Copie essa string gerada, e abra o [Jenkins], cole essa string no campo que está sendo solicitado.
Criar uma conta de usuario e avance.

Configurar Maven
Gerenciar Jenkins > Global Tool Configuration > Maven
    -> Maven instalações...
    defina o nome como M3 e salve

Configurar novo Job
Novo Job
    -> digite um nome para o job
    -> selecione a opção pipeline
    -> ok

    -> seleciona as seguintes opções
        - Consultar periodicamente o SCM 
          -> defina o seguinte valor H/15 * * * * (ele irá buscar atualizações na branch a cada 15m)
    -> Pipeline
        -> selecione o Pipeline script from SCM
            -> SCM 
                -> selecione Git
                    -> configure o repositorio
                    -> selecione a branch que vai ser observada
            -> Script Path
                -> defina o diretorio e o nome do arquivo com o pipeline do jenkins
    -> salvar


[Docker]: <https://docs.docker.com/get-docker/>
[Docker Compose]: <https://docs.docker.com/compose/>
[Konga]: <http://localhost:1337/>
[Jenkins]: <http://localhost:8080/>