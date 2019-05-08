#DJANGO NEWSLETTER APP
Just template for web app on django web framework. Includes full user authentication and authorization flow.
Articles and comments are just example.
Contains three apps:
1) articles - newsletter CRUD
2) users - user flow
3) pages - main pages and routes for app

#System requirements
* python 3.6.6+
* pipenv
* Docker 18+ && docker-compose

# Installation steps
At first build docker container
```bash
$ docker build .
$ docker-compose run web python /code/manage.py migrate --noinput
```

Define a superuser:
```bash
$ docker-compose run web python /code/manage.py createsuperuser
```

And finally, apply the last changes,
```bash
$ docker-compose up -d --build
```

The site will be able on `0.0.0.0:8000`

# How to stop server
There are two docker containers for this app: db and web, you can find it via
```bash
$ docker ps
``` 
The output should be like this:
```bash
CONTAINER ID        IMAGE                                                 COMMAND                  CREATED             STATUS              PORTS                                                                                                                  NAMES
b589c219c11b        postgres:10.1-alpine                                  "docker-entrypoint.s…"   29 minutes ago      Up 8 minutes        5432/tcp
4580c219eeee        web:latest                                            "docker-entrypoint.s…"   29 minutes ago      Up 8 minutes        0.0.0.0:8000->8000/tcp 

```
Just copy CONTAINER ID of container(s) you want to delete and run
```bash
$ docker stop b589c219c11b 4580c219eeee
```
