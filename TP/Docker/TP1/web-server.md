# TP Docker – Étape 3 : Serveur web avec index.html

## Objectif

Exécuter un serveur web (nginx) dans un conteneur Docker (ou Podman) et y servir une page `index.html` locale :

1. Avec un **volume partagé**
2. Avec la commande **`docker cp`**

---

## Étapes

### 1. Récupération de l'image nginx

```bash
docker pull docker.io/library/nginx
```

---

### 2. Vérification de la présence de l’image en local

```bash
docker images
```

---

### 3. Création de la page HTML à servir

```bash
mkdir ~/tp-docker
cd ~/tp-docker

echo "<h1>Bonjour depuis Docker !</h1>" > index.html
```

---

### 4. Démarrage du conteneur nginx avec un volume

```bash
docker run -d -p 8080:80 -v $(pwd)/index.html:/usr/share/nginx/html/index.html docker.io/library/nginx
```

- `-v` permet de lier le fichier local au conteneur.
- Accès : http://localhost:8080

---

### 5. Suppression du conteneur

```bash
docker ps            # pour identifier le conteneur
docker stop <ID>     # remplace <ID> par l'identifiant ou le nom du conteneur
docker rm <ID>
```

---

### 6. Démarrage d’un nouveau conteneur nginx

```bash
docker run -d -p 8080:80 docker.io/library/nginx
```

---

### 7. Copie du fichier HTML dans le conteneur

```bash
docker ps                        # récupérer l'ID ou le nom du conteneur
docker cp index.html <ID>:/usr/share/nginx/html/index.html
```

- Remplace `<ID>` par l’ID ou le nom du conteneur.

---

## Résultat attendu

Dans les deux cas (`-v` et `docker cp`), accéder à :

```
http://localhost:8080
```

Tu dois voir le message : **"Bonjour depuis Docker !"**

---

## Fichiers liés

- `index.html` : page HTML à servir
- `web-server.md` : ce fichier

