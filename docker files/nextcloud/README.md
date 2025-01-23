# EN

## Information

Nextcloud is a private cloud solution that allows anyone to set up a cloud storage system at home, accessible to everyone. The goal is to eliminate reliance on large corporations.

## Setting up the cloud

To set up this service, you will need Docker and Docker Compose, which make it easy to deploy software. Here is the file to use :

```
volumes:
  nextcloud:
  db:

services:
  db:
    image: mariadb:10.6
    restart: always
    command: --transaction-isolation=READ-COMMITTED --log-bin=binlog --binlog-format=ROW
    volumes:
      - db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=${YourPassword!}
      - MYSQL_PASSWORD=${YourPassword!}
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud

  app:
    image: nextcloud
    restart: always
    ports:
      - 8080:80
    links:
      - db
    volumes:
      - nextcloud:/var/www/html
    environment:
      - MYSQL_PASSWORD=${YourPassword!}
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=db
```



# FR

## Informations

Nextcloud est un cloud privé permettant à chacun de mettre en place un espace de stockage en ligne chez soi, accessible à tous. L'objectif est de ne plus dépendre des grandes entreprises.

## Mise en place du cloud

Pour mettre en place ce service, vous aurez besoin de Docker et Docker Compose, qui permettent de déployer facilement des logiciels. Voici le fichier à utiliser :

```
volumes:
  nextcloud:
  db:

services:
  db:
    image: mariadb:10.6
    restart: always
    command: --transaction-isolation=READ-COMMITTED --log-bin=binlog --binlog-format=ROW
    volumes:
      - db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=${YourPassword!}
      - MYSQL_PASSWORD=${YourPassword!}
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud

  app:
    image: nextcloud
    restart: always
    ports:
      - 8080:80
    links:
      - db
    volumes:
      - nextcloud:/var/www/html
    environment:
      - MYSQL_PASSWORD=${YourPassword!}
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=db
```


