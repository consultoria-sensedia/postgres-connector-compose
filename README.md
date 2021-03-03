# Docker-compose para Sensedia API Connector Postgres

Repositório com configuração para subir Sensedia API Connector para PostgreSQL.

```sh
#'cd' no diretório dos arquivos
#Configurar CONNECTOR_ID, CONNECTOR_FACTOR no .env

#subirá: 
# postgres (usuário, senha e banco padrão: database)
# sensedia/postgres-db-9.4-conn
# Ngrok (opcional)
# Adminer (opcional)

sudo docker-compose up 

#Se utilizando Ngrok, colar a url gerada no "endpoint" do Connector, no Manager.
```
http://localhost:4040 -> [Ngrok](https://ngrok.com/) (exporta serviço localhost para URL pública)

http://localhost:8080 -> [Adminer](https://www.adminer.org/) (Cliente BD)


## Referências
[Documentação API Connectors](https://help.v3.apisuite.sensedia.com/pt/api-platform-guide/4.3.x.x/api-connectors/api-connectors.html)

[Imagem PqSQL Connector DockerHub](https://hub.docker.com/r/sensedia/postgres-db-9.4-conn)
