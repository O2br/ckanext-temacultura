# Tema cultura
## Extensão do CKAN com os tema do Ministério da cultura

## Instalação

1. Rodar o docker-compose up na pasta do projeto

```
docker-compose up
```

2. entrar no container do ckan

```
docker exec -it [ID] /bin/bash
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


## Atualização:

1. entrar no container do ckan

```
docker exec -it [ID] /bin/bash
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
