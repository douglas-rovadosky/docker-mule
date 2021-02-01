# Integration System Framework

Componentes para a criação das imagens e das configurações necessárias para aplicação Integration System Framework.

### Requisitos
* [Docker] - Open platform for developing, shipping, and running applications
* [Docker Compose] - Tool for defining and running multi-container Docker applications.

<!-- ### Configurações necessárias -->
<!-- Altere as configurações de autenticação do _composer_ localizadas no arquivo _docker/magento-php/auth.json_. -->
<!-- Substitua o valor __<public-key>__ na propriedade _username_ pelo valor da sua PublicKey e a __<secret-key>__ na propriedade _password_ pelo valor da sua SecretKey, ambas geradas no MarketPlace do Magento. -->
<!-- Acessse [Get your authentication keys](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) e siga as instruções para criação das credenciais. -->

<!-- É necessário adicionar o host __local.magento__ nos hosts do seu sistema operacional. -->

### Instalação
Iniciar os containers:
```sh
$ docker-compose up -d
```
Validar se os containers estão rodando:
```sh
$ docker ps
```


[Docker]: <https://docs.docker.com/get-docker/>
[Docker Compose]: <https://docs.docker.com/compose/>