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
