# TP Docker – Installation sur Parrot OS

## ✅ Objectif
Installer et vérifier le bon fonctionnement de Docker et Docker Compose sur une distribution Parrot OS.

---

# Installation de Docker
---

### 📦 Mise à jour du système

```bash
sudo apt update && sudo apt upgrade -y
```

---

### 🧰 Installation des dépendances

```bash
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release -y
```

---

### 🔐 Ajout de la clé GPG Docker

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

---

### ➕ Ajout du dépôt Docker

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

### 🐳 Installation de Docker Engine

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

---

### ▶️ Test de fonctionnement Docker

```bash
sudo systemctl status docker
sudo docker run hello-world
```

---

### 🧩 Installation de Docker Compose

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

---

### 🧪 Vérification

```bash
docker-compose --version
```

---