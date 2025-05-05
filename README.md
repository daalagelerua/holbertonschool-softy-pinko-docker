# holbertonschool-softy-pinko-docker

## Instructions principales d'un Dockerfile

 Ces instructions permettent de définir comment construire une image Docker.

### FROM - Définit l'image de base
```
FROM ubuntu:22.04
```

### LABEL - Ajoute des métadonnées(informations qui décrivent, expliquent ou contextualisent d'autres données) à l'image
```
LABEL maintainer="email@example.com"
LABEL version="1.0"
```

### RUN - Exécute des commandes pendant la construction de l'image
```
RUN apt-get update && apt-get install -y nginx
```

### COPY - Copie des fichiers depuis votre machine vers l'image
```
COPY app.py /app/
```

### ADD - Similaire à COPY mais avec des fonctionnalités supplémentaires (extraction d'archives, URLs)
```
ADD archive.tar.gz /app/
```

### WORKDIR - Définit le répertoire de travail pour les instructions qui suivent
```
WORKDIR /app
```

### ENV - Définit des variables d'environnement
```
ENV NODE_ENV=production
```

### ARG - Définit des variables utilisables pendant la construction
```
ARG VERSION=latest
```

### EXPOSE - Informe Docker que le conteneur écoute sur les ports spécifiés
```
EXPOSE 80 443
```

### CMD - Définit la commande par défaut exécutée au démarrage du conteneur
```
CMD ["nginx", "-g", "daemon off;"]
```

### ENTRYPOINT - Configure le conteneur pour qu'il s'exécute comme une commande
```
ENTRYPOINT ["python", "app.py"]
```

### VOLUME - Crée un point de montage pour des volumes externes
```
VOLUME /data
```

### USER - Définit l'utilisateur qui exécutera les commandes suivantes
```
USER nginx
```

### HEALTHCHECK - Définit une commande pour vérifier la santé du conteneur
```
HEALTHCHECK --interval=5m CMD curl -f http://localhost/ || exit 1
```

### SHELL - Change l'interpréteur de commandes par défaut
```
SHELL ["/bin/bash", "-c"]
```

### STOPSIGNAL - Définit le signal système pour arrêter le conteneur
```
STOPSIGNAL SIGTERM
```

## Rôle des directives proxy_set_header

Les directives proxy_set_header permettent de transmettre des informations importantes sur la requête d'origine aux serveurs backend.

1 - `proxy_set_header Host $host` :

Transmet le nom d'hôte original de la requête
Sans cela, le serveur backend recevrait le nom du serveur proxy comme hôte


2 - `proxy_set_header X-Real-IP $remote_addr` :

Envoie l'adresse IP réelle du client au serveur backend
Permet au backend de connaître l'origine véritable de la requête


3 - `proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for` :

Maintient une liste des adresses IP par lesquelles la requête a transité
Utile pour le traçage et les journaux d'accès


4 - `proxy_set_header X-Forwarded-Proto $scheme` :

Indique au backend quel protocole (HTTP ou HTTPS) a été utilisé par le client
Important pour la génération d'URLs correctes par le backend

### Conclusion

Ces en-têtes sont une pratique standard lors de la configuration d'un proxy inverse et garantissent que vos applications backend reçoivent toutes les informations nécessaires pour fonctionner correctement, malgré la présence d'un intermédiaire (le proxy) entre le client et le serveur.