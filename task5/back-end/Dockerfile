# Utilisation de l'image Ubuntu la plus récente comme base
FROM ubuntu:latest

# Mise à jour des dépôts APT
RUN apt-get update

# Mise à niveau des logiciels installés
RUN apt-get upgrade -y

# Installation de Python3 et pip3
RUN apt-get install -y python3 python3-pip

# Résolution du problème "externally managed"
RUN rm /usr/lib/python*/EXTERNALLY-MANAGED

# Installation de Flask via pip3
RUN pip3 install flask flask-cors

# Définition du répertoire de travail
WORKDIR /app

# Copie du fichier Python dans le conteneur
COPY api.py /app/

# Exposition du port 5252
EXPOSE 5252

# Commande à exécuter lorsque le conteneur démarre
CMD ["python3", "api.py"]
