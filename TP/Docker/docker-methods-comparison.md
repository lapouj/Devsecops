# TP Docker – Comparaison des méthodes : `-v`, `docker cp` et `Dockerfile`

## Objectif

Comprendre les différences entre trois façons de servir un fichier dans un conteneur Docker :
- `-v` : liaison de fichier (volume)
- `docker cp` : copie manuelle dans un conteneur
- `Dockerfile` : image personnalisée

---

## 1. `-v` – Volume (liaison de fichier local)

### Commande :

```bash
docker run -d -p 8080:80 -v $(pwd)/index.html:/usr/share/nginx/html/index.html nginx
```

### Fonctionnement :
- Lie un fichier de l’hôte (machine locale) au conteneur
- Pas de modification de l’image
- Les changements locaux sont visibles en live dans le conteneur

### Avantages :
- Rapide à mettre en place
- Idéal pour le développement

### Inconvénients :
- Non portable (le fichier reste sur ta machine)
- Incompatible avec certains déploiements distants (CI/CD, cloud)

---

## 2. `docker cp` – Copier un fichier dans un conteneur en cours

### Commande :

```bash
docker cp index.html <ID>:/usr/share/nginx/html/index.html
```

### Fonctionnement :
- Copie un fichier dans un conteneur déjà en cours d'exécution
- Le fichier est injecté dans le conteneur, mais ne modifie pas l’image

### Avantages :
- Facile à faire une fois le conteneur lancé
- Pas besoin de rebuild

### Inconvénients :
- Non versionné
- Nécessite une action manuelle à chaque exécution
- Pas adapté à la production ou à l’automatisation

---

## 3. `Dockerfile` – Création d'une image personnalisée

### Exemple de Dockerfile :

```dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html/index.html
```

### Build et exécution :

```bash
docker build -t custom-nginx .
docker run -d -p 8080:80 custom-nginx
```

### Fonctionnement :
- Crée une nouvelle image Docker avec tous les fichiers intégrés
- Reproductible et portable

### Avantages :
- Reproductible et versionnable
- Idéal pour le partage, la CI/CD, la production
- Plus flexible et propre

### Inconvénients :
- Nécessite un build à chaque modification

---

## Résumé comparatif

| Méthode        | Image modifiée ? | Persistance | Portabilité | Usage typique              |
|----------------|------------------|-------------|--------------|-----------------------------|
| `-v`           | ❌ Non            | Oui (local) | ❌ Non       | Développement local         |
| `docker cp`    | ❌ Non            | Temporaire  | ❌ Non       | Tests manuels, debug rapide |
| `Dockerfile`   | ✅ Oui            | Oui         | ✅ Oui       | CI/CD, production, partage  |

---

## Conclusion

- Utiliser `-v` pour tester localement avec des fichiers qui changent souvent
- Utiliser `docker cp` pour injecter ponctuellement un fichier
- Utiliser `Dockerfile` pour une solution propre, maintenable et déployable

