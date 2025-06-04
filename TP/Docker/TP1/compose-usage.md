# TP Docker – Étape 8 : Utilisation de Docker Compose

## Objectif

Utiliser `docker-compose` pour orchestrer plusieurs conteneurs Docker (MySQL + phpMyAdmin) à partir d’un seul fichier de configuration.

---

## 1. Contenu du fichier `docker-compose.yml`

```yaml
version: '3.8'

services:
  mysql:
    image: docker.io/library/mysql:5.7
    container_name: mysql57
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: tpdocker
      MYSQL_USER: user
      MYSQL_PASSWORD: user
    networks:
      - tpnet

  phpmyadmin:
    image: docker.io/phpmyadmin/phpmyadmin
    container_name: mypma
    ports:
      - "8081:80"
    environment:
      PMA_HOST: mysql
    depends_on:
      - mysql
    networks:
      - tpnet

networks:
  tpnet:
```

---

## 2. Lancement de l’environnement

```bash
docker-compose up -d
```

- `-d` : mode détaché (background)
- Lance tous les services déclarés dans `docker-compose.yml`

---

## 3. Vérification

```bash
docker ps
```

Les conteneurs `mysql57` et `mypma` doivent apparaître comme actifs.

---

## 4. Accès à phpMyAdmin

- URL : http://localhost:8081
- Hôte : `mysql`
- Utilisateur : `user`
- Mot de passe : `user`

---

## 5. Arrêt des services

```bash
docker-compose down
```

---

## 6. Questions & Réponses

### a. Qu’apporte le fichier `docker-compose` par rapport aux commandes `docker run` ? Pourquoi est-il intéressant ?

- Il centralise la configuration de plusieurs conteneurs dans **un seul fichier lisible et versionnable**.
- Il permet de **démarrer toute une architecture** (réseaux, services, variables) avec une **simple commande** (`docker-compose up`).
- Il rend le projet **portable et reproductible** : n'importe qui peut relancer exactement la même stack avec le fichier YAML.

### b. Quel moyen permet de configurer (premier utilisateur, première base de données, mot de passe root, …) facilement le conteneur MySQL au lancement ?

- Grâce aux **variables d’environnement** :
  - `MYSQL_ROOT_PASSWORD`
  - `MYSQL_DATABASE`
  - `MYSQL_USER`
  - `MYSQL_PASSWORD`
- Ces variables sont passées dans le bloc `environment:` du service `mysql`.

---

## Fichiers associés

- `docker-compose.yml` : configuration multi-conteneurs
- `compose-usage.md` : ce fichier

