# TP Docker – Étape 9 : Isolation réseau entre conteneurs

## Objectif

Créer une architecture Docker avec 3 conteneurs (`web`, `app`, `db`) et 2 réseaux (`frontend`, `backend`) afin d'observer l'isolation réseau entre services.

---

## 1. Fichier `docker-compose.yml` (extrait)

```yaml
version: '3.8'

services:
  web:
    image: praqma/network-multitool
    container_name: web
    networks:
      - frontend

  app:
    image: praqma/network-multitool
    container_name: app
    networks:
      - frontend
      - backend

  db:
    image: praqma/network-multitool
    container_name: db
    networks:
      - backend

networks:
  frontend:
  backend:
```

---

## 2. Lancement des conteneurs

```bash
docker-compose up -d
```

---

## 3. Tests de connectivité (ping)

### Depuis `web`

```bash
docker exec -it web sh
ping db   # Résultat attendu : échec
```

### Depuis `app`

```bash
docker exec -it app sh
ping db   # Résultat attendu : OK
```

- Le conteneur `web` ne voit pas `db` car ils ne partagent **aucun réseau**
- Le conteneur `app` voit `db` car ils partagent le réseau `backend`

---

## 4. Vérification avec `docker inspect`

```bash
docker inspect web
docker inspect db
```

- Regarder la section `"Networks"` dans les résultats
- Justification : les conteneurs sont connectés uniquement aux réseaux déclarés dans `docker-compose.yml`

---

## 5. Cas d’usage réel

### Exemple concret :

| Service | Rôle              | Réseau(s)          | Sécurité                     |
|---------|-------------------|--------------------|------------------------------|
| web     | Frontend statique | `frontend`         | Public mais isolé de la DB   |
| app     | Backend API       | `frontend`, `backend` | Pont entre web et base      |
| db      | Base de données   | `backend`          | Privée, non accessible du web|

Ce type d’isolation est utilisé en production pour :
- **Limiter les accès** réseau entre composants
- **Séparer les responsabilités**
- **Réduire la surface d’attaque**

---

## Questions & Réponses

### a. Quelles lignes du résultat de `docker inspect` justifient ce comportement ?

Les lignes situées dans :

```json
"Networks": {
  "frontend": { ... },
  "backend": { ... }
}
```

Elles montrent à quels réseaux chaque conteneur appartient. Par exemple :
- `web` → uniquement `frontend`
- `db` → uniquement `backend`
- `app` → les deux

---

### b. Dans quelle situation réelle (avec quelles images) pourrait-on avoir cette configuration réseau ? Dans quel but ?

#### Exemple réel :

- `nginx` en frontend
- `node` ou `spring-boot` en backend
- `mysql` ou `postgres` en base

#### Objectifs :

- **Sécurité** : `db` n’est jamais exposée publiquement
- **Modularité** : les couches (web/app/db) sont découplées
- **Contrôle réseau** : chaque couche ne parle qu’à ce qu’elle doit connaître

---

## Fichiers associés

- `docker-compose.yml` : configuration réseau et services
- `network-isolation.md` : ce fichier

