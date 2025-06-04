# TP Docker – Étape 7 : MySQL + phpMyAdmin dans des conteneurs

## Objectif

Exécuter une base de données MySQL (v5.7) et une interface web phpMyAdmin dans des conteneurs Docker/Podman, en les connectant via un réseau personnalisé.

---

## 1. Récupération des images (Podman/Docker avec noms complets)

```bash
docker pull docker.io/library/mysql:5.7
docker pull docker.io/phpmyadmin/phpmyadmin
```

> ⚠️ Sous Podman, les noms courts comme `mysql:5.7` ne sont pas reconnus. Utiliser les noms complets depuis `docker.io`.

---

## 2. Création d’un réseau personnalisé

```bash
docker network create tp-net
```

---

## 3. Lancement du conteneur MySQL

```bash
docker run -d --name mysql57 --network tp-net \
  -e MYSQL_ROOT_PASSWORD=rootpass \
  -e MYSQL_DATABASE=tpdocker \
  -e MYSQL_USER=tpuser \
  -e MYSQL_PASSWORD=tppass \
  docker.io/library/mysql:5.7
```

### Explication des variables :
- `MYSQL_ROOT_PASSWORD` : mot de passe du superutilisateur
- `MYSQL_DATABASE` : base créée automatiquement
- `MYSQL_USER` et `MYSQL_PASSWORD` : utilisateur secondaire

---

## 4. Lancement du conteneur phpMyAdmin

```bash
docker run -d --name mypma --network tp-net -p 8081:80 \
  -e PMA_HOST=mysql57 \
  docker.io/phpmyadmin/phpmyadmin
```

### Accès :

- URL : http://localhost:8081
- Nom d’hôte : `mysql57`
- Utilisateur : `tpuser`
- Mot de passe : `tppass`

> Possibilité de se connecter avec `root` / `rootpass`

---

## 5. Création manuelle d’une table

1. Aller sur phpMyAdmin
2. Sélectionner la base `tpdocker`
3. Créer une table `utilisateurs` avec des colonnes comme :
   - `id` INT AUTO_INCREMENT PRIMARY KEY
   - `nom` VARCHAR(50)
   - `email` VARCHAR(100)
4. Ajouter quelques lignes

---

## Résultat attendu

- Deux conteneurs en fonctionnement (`mysql57` et `mypma`)
- Interface phpMyAdmin fonctionnelle
- Table `utilisateurs` avec des données insérées

---

## Fichiers liés

- `mysql-phpmyadmin.md` : ce fichier
