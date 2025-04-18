# FR

## Installation
Pour pouvoir installer et utiliser Vaultwarden, vous devrez créer un certificat autosigné afin de permettre de passer votre site en HTTPS. Vous pouvez le faire avec Traefik, mais nous allons voir comment procéder avec un certificat autosigné créé avec OpenSSL.
Voici les commandes à exécuter pour préparer l'environnement
```
mkdir -p /opt/vaultwarden/ssl
cd /opt/vaultwarden/ssl
openssl genrsa -out vaultwarden.key 2048
openssl req -new -x509 -key vaultwarden.key -out vaultwarden.crt -days 3650
```

Si vous souhaitez ne pas mettre les certificats et les clés dans le répertoire actuel (/opt/vaultwarden/ssl), il suffira simplement de modifier l'emplacement des fichiers dans la section "Volume" du fichier docker-compose  !

# EN

## Installation
To install and use Vaultwarden, you will need to create a self-signed certificate to enable HTTPS for your site. While this can be done with Traefik, we will go through the process of creating a self-signed certificate using OpenSSL.
Here are the commands to execute in order to prepare the environment : 
```
mkdir -p /opt/vaultwarden/ssl
cd /opt/vaultwarden/ssl
openssl genrsa -out vaultwarden.key 2048
openssl req -new -x509 -key vaultwarden.key -out vaultwarden.crt -days 3650
```

If you prefer not to store the certificates and keys in the current directory (/opt/vaultwarden/ssl), you simply need to change the file locations in the "Volume" section of the docker-compose file!
