# TP Docker – Installation sur Parrot OS

## Objectif

Installer Docker et Docker Compose sur une distribution Parrot OS, basée sur Debian, en contournant l'erreur liée à l'absence de support officiel du dépôt `lory`.

---

## Étape 1 – Mise à jour du système

On met à jour les index de paquets et les paquets installés :

```bash
sudo apt update && sudo apt upgrade -y
```

---

## Étape 2 – Installation des dépendances nécessaires

Ces paquets sont nécessaires pour que `apt` puisse télécharger depuis des dépôts sécurisés via HTTPS et gérer les clés :

```bash
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release -y
```

---

## Étape 3 – Ajout de la clé GPG officielle de Docker

Cette clé permet de vérifier l'authenticité des paquets téléchargés depuis le dépôt Docker :

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | \
sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

---

## Étape 4 – Ajout du dépôt Docker (compatible Debian Bookworm)

### Supprimer l'ancien dépôt Docker (si présent)

```bash
sudo rm /etc/apt/sources.list.d/docker.list
```

### Ajouter manuellement le dépôt avec `bookworm`

```bash
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
https://download.docker.com/linux/debian bookworm stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

## Étape 5 – Mise à jour des dépôts

```bash
sudo apt update
```

---

## Étape 6 – Installation de Docker Engine

```bash
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

---

## Étape 7 – Vérification du fonctionnement

### Vérifier que Docker est bien actif

```bash
sudo systemctl status docker
```

### Tester avec un conteneur

```bash
sudo docker run hello-world
```

---

## Étape 8 – Installation de Docker Compose

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

---

## Étape 9 – Vérification Docker Compose

```bash
docker-compose --version
```

---

## État attendu avant de continuer le TP

- `docker --version` ✅
- `docker-compose --version` ✅
- `docker run hello-world` fonctionne ✅

