# Tema cultura

Extensão do CKAN com o tema do Ministério da cultura

## Instalação

1. Rodar o docker-compose up na pasta do projeto

```
docker-compose up
```

2. entrar no container do ckan

```
docker exec -it ckan /bin/bash
```

1. Ativar o ambiente virtual:

```
. /usr/lib/ckan/default/bin/activate
```

2. instalar o tema no ambiente:

```
cd /usr/lib/ckan/default/src/ckanext-temacultura

pip install .
```

3. inserir a extensão no ckan.ini, na linha de plugins

```
vim /etc/ckan/default/ckan.ini

ckan.plugins = stats text_view image_view recline_view temacultura
```

4. restart no docker-compose (não tem como restartar o paster pois ele é o entrypoint do container (Pid1)
```
ctrl + c (caso a saída do compose esteja ligada ao seu sysout)
ou
docker-compose restart
```

PS:  
Tem que instalar o vim no container (shame -_-")

## Atualização:

1. entrar no container do ckan

```
docker exec -it ckan /bin/bash
```

2. Ativar o ambiente virtual:

```
. /usr/lib/ckan/default/bin/activate
```

3. entrar na pasta do projeto

```
cd /usr/lib/ckan/default/src/ckanext-temacultura
```

4. rodar o install (build) da extensão:

```
pip install . --upgrade
```

PS:  
grande parte disso pode ser automatizado, podemos fazer isso para a próxima release <3

## Criando users admins e datasets de teste (ambiente dev)

1. entrar no container ckan

```
docker exec -it ckan /bin/bash
```

2. modificar a url de acesso ao banco (está errada nesse arquivo de configuraçes):

```
vim /etc/ckan/default/ckan.ini

sqlalchemy.url = postgresql://ckan:ckan@db/ckan

# caso use o comando de criação de datasets
solr_url =http://solr:8983/solr/ckan
```

3. rodar o comando de criação de admin ou criação da base de testes

```
ckan-paster --plugin=ckan sysadmin add admin --config=/etc/ckan/default/development.ini
ou
ckan-paster --plugin=ckan create-test-data -c /etc/ckan/default/development.ini
```
