# TP Docker – Étape 2 : Commandes de base

## Objectif

Découvrir les commandes essentielles de Docker (via Podman sur Parrot OS) pour manipuler des images et des conteneurs.

---

## Environnement

> ⚠️ Parrot OS utilise **Podman**, un moteur de conteneurisation compatible Docker, mais en mode **rootless** (sans privilèges root). Cela a un impact notamment sur l’usage des ports < 1024.

---

## Commandes testées

### 1. Hello World

```bash
docker run hello-world
```

- Télécharge une image de test.
- Vérifie que le moteur de conteneurisation fonctionne correctement.

---

### 2. Terminal interactif dans un conteneur Ubuntu

```bash
docker run -it ubuntu bash
```

- Lance un conteneur Ubuntu avec un shell interactif.
- Pour quitter : `exit` ou `Ctrl+D`.

#### Variante Debian

```bash
docker run -it debian bash
```

- Debian est plus minimaliste que Ubuntu.
- Peut nécessiter l'installation manuelle d'outils comme `curl`, `ping`, etc.

---

### 3. Lister les images locales

```bash
docker images
```

- Affiche les images téléchargées ou construites localement.

---

### 4. Lister tous les conteneurs (actifs ou non)

```bash
docker ps -a
```

- Liste tous les conteneurs, y compris ceux qui sont arrêtés.

---

### 5. Exécuter un serveur NGINX

#### ⚠️ Problème avec les images en "short name"

Sur Podman, il faut spécifier le registre complet pour certaines images :

```bash
docker run -p 8080:80 docker.io/library/nginx
```

- Le port 80 du conteneur est mappé au port 8080 de l’hôte.
- Accès : http://localhost:8080

#### Version en arrière-plan (détachée)

```bash
docker run -d -p 8080:80 docker.io/library/nginx
```

---

## Problème rencontré : port 80 interdit

### Message d'erreur

```
rootlessport cannot expose privileged port 80
```

> Sous Podman, les ports < 1024 ne sont pas utilisables sans configuration spéciale, car ils sont considérés comme "privilégiés".

---

## Solutions

### Solution 1 – Utiliser un port >= 1024 (recommandée)

```bash
docker run -p 8080:80 docker.io/library/nginx
```

---

### Solution 2 – Autoriser les ports < 1024 (optionnelle)

1. Éditer le fichier `/etc/sysctl.conf` :

```bash
sudo nano /etc/sysctl.conf
```

2. Ajouter la ligne :

```ini
net.ipv4.ip_unprivileged_port_start=80
```

3. Appliquer la configuration :

```bash
sudo sysctl -p
```

---

## Images utilisées

- `hello-world`
- `ubuntu`
- `debian`
- `docker.io/library/nginx`

---

## Fichiers liés

- `README.md` : instructions d'installation Docker (étape 1)
- `docker-commands.md` : ce fichier
