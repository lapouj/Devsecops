# 🧠 Projet personnel – Analyse DevSecOps

## 📌 Contexte du projet

- **Nom du projet** : [Nom de ton projet]
- **Type de projet** : [Web, API, Mobile, Automatisation, Infra, etc.]
- **Durée** : [Ex. 2 mois]
- **Technos utilisées** : [Langages, outils, plateformes, etc.]
- **Objectif du projet** :  
  > Décris en 2-3 phrases ce que le projet faisait, son intérêt personnel ou professionnel.

---

## 🔁 Adaptation au cycle DevSecOps

### Phase 1 – 🗂️ PLAN

- **Ce que j’ai fait** :
  > [As-tu planifié ton projet ? Écrit des specs ? Anticipé des risques ?]

- **Ce qui était adapté** ✅ :
  > [Ex. : j’ai réfléchi aux besoins de sécurité dès le début, j’ai identifié les utilisateurs...]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : je n’ai pas pensé aux risques de sécurité, ni défini de backlog sécurité.]

---

### Phase 2 – 💻 CODE

- **Ce que j’ai fait** :
  > [Ton organisation du code, outils utilisés, bonnes pratiques]

- **Ce qui était adapté** ✅ :
  > [Ex. : séparation des secrets, utilisation de `bandit`, clean code...]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : j’ai laissé des credentials dans un `.env` versionné]

---

### Phase 3 – 🔨 BUILD

- **Ce que j’ai fait** :
  > [Comment tu as compilé, packagé, conteneurisé ton app]

- **Ce qui était adapté** ✅ :
  > [Ex. : utilisation de Docker, build reproductible...]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : pas de scan des images, pas de versioning clair]

---

### Phase 4 – 🧪 TEST

- **Ce que j’ai fait** :
  > [Types de tests faits : unitaires, intégration, manuels, automatisés]

- **Ce qui était adapté** ✅ :
  > [Ex. : j’ai utilisé `pytest`, fait des tests sur les erreurs, etc.]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : pas de tests de sécurité automatisés, pas de test de dépendances]

---

### Phase 5 – 🚀 RELEASE

- **Ce que j’ai fait** :
  > [Comment tu validais une version prête à être livrée]

- **Ce qui était adapté** ✅ :
  > [Ex. : tagging, changelog, stockage des artefacts...]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : pas de politique de release, aucune vérification finale]

---

### Phase 6 – 📦 DEPLOY

- **Ce que j’ai fait** :
  > [Ton mode de déploiement : FTP, Docker, CI/CD ?]

- **Ce qui était adapté** ✅ :
  > [Ex. : déploiement via pipeline, séparé entre dev/prod...]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : pas de rollback possible, secrets dans le Dockerfile...]

---

### Phase 7 – ⚙️ OPERATE

- **Ce que j’ai fait** :
  > [Ton projet fonctionnait-il 24/7 ? As-tu fait du monitoring manuel ?]

- **Ce qui était adapté** ✅ :
  > [Ex. : logs stockés, version des services contrôlée...]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : pas de durcissement OS, peu de surveillance système]

---

### Phase 8 – 🔍 MONITOR

- **Ce que j’ai fait** :
  > [Tu as surveillé ton app ? Mis en place des alertes ou des logs ?]

- **Ce qui était adapté** ✅ :
  > [Ex. : journaux d’erreurs analysés, dashboard rudimentaire]

- **Ce que j’aurais pu améliorer** ⚠️ :
  > [Ex. : pas d’alertes en cas de bug ou faille, logs non centralisés]

---

## 🎯 Bilan général

- **Points forts de mon approche DevSecOps** :
  > [Liste claire : ex. bonne séparation des environnements, code sécurisé, CI/CD utilisé…]

- **Faiblesses identifiées** :
  > [Ce que tu ferais différemment aujourd’hui, avec plus de maturité DevSecOps]

- **Ce que j’ai appris** :
  > [Ton retour d’expérience, lien avec la sécurité, l’automatisation, la collaboration]

---

## 📌 Pistes d’amélioration concrètes

1. Ajouter un pipeline CI/CD avec des scans (`Semgrep`, `Trivy`, `Bandit`)
2. Intégrer un outil de monitoring (`Grafana`, `Prometheus`, `ELK`)
3. Utiliser `Vault` pour la gestion des secrets
4. Modéliser les menaces (STRIDE) en phase de planification
5. Documenter les incidents et décisions pour audit futur

---

## 📄 Annexes (facultatives)

- Lien vers le dépôt Git : [URL]
- Exemple de Dockerfile ou `.gitlab-ci.yml`
- Screenshot du projet
