# docker-learning

### Constroi o container
* docker-compose build \<service\>

### Roda o container
* docker-compose up \<service\>

## docker-compose.yml
```
version: "3.4"

services:
  nodejs:
    container_name: nodejs
    build:
      context:  ./nodejs-javascript/
      target: debug
    volumes:
    - ./nodejs-javascript/src/:/work/src/
    ports:
      - 9999:5000 
      - 9229:9229

...
```
### Detalhes do docker-compose
```
...
    build:
      context:  ./nodejs-javascript/
      target: debug
...
```
* __target:__ Indica qual stage será construido do Dockerfile

```
...
volumes:
    - ./nodejs-javascript/src/:/work/
...
```
* __volumes:__ Mapeia os diretórios que serão usados para mapear os arquivos para debug no host e no container

```
...
    ports:
      - 9999:5000 
      - 9229:9229
...
```
* __ports:__ Correlaciona as portas do host:container, no exemplo acima a porta 9999 do host está vinculada a porta 5000 do container

