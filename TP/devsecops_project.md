# 🧠 Projet personnel – Analyse DevSecOps

## 📌 Contexte du projet

- **Nom du projet** : Création d'un site e-commerce de vente de perles, en tant que dév dans une agence web.
- **Type de projet** : Site marchand Prestashop.
- **Durée** : Environ 8 semaines, suivi continue par la suite pour les mise à jour et demandes de modification.
- **Technos utilisées** : Prestashop, PHP, MySQL, HTML, CSS, JavaScript, FTP, OVH, TLS/SSL.
- **Objectif du projet** :  
Développer un site e-commerce pour une cliente vendant des perles et bijoux, permettant la gestion de ses produits, des paiements en ligne, du catalogue et des commandes via un back-office accessible.

---

## 🔁 Adaptation au cycle DevSecOps

### Phase 1 – 🗂️ PLAN

- **Ce que j’ai fait** :  
Le projet a été planifié de manière assez informelle, via un Google Drive partagé et des réunions orales hebdomadaires. Les besoins de la cliente étaient souvent transmis par téléphone.

- **Ce qui était adapté** ✅ :  
  - Présence d’un planning général
  - Communication hebdomadaire régulière avec l’équipe

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Absence de gestion formelle des risques
  - Pas de trace écrite systématique des besoins ou des changements
  - Aucune prise en compte de la sécurité dès la planification (pas de backlog sécurité, pas de modélisation de menaces)

---

### Phase 2 – 💻 CODE

- **Ce que j’ai fait** :  
J’ai développé en PHP, HTML, CSS, JS, en m’appuyant sur WordPress et WooCommerce, avec parfois des modifications directes dans les thèmes.

- **Ce qui était adapté** ✅ :  
  - Utilisation d’un thème enfant pour éviter d’écraser les modifications
  - Respect des langages standard du web

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Modifications de fichiers sensibles directement en prod sans versioning
  - Aucun dépôt Git ou suivi de version
  - Pas de revue de code ni gestion collaborative

---

### Phase 3 – 🔨 BUILD

- **Ce que j’ai fait** :  
Pas de processus de build automatisé. Le site était assemblé via des plugins, des fichiers PHP/CSS personnalisés, puis envoyé via FTP.

- **Ce qui était adapté** ✅ :  
  - Structure technique cohérente à l’échelle du CMS

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Aucun pipeline de build, aucun scan des plugins ou des dépendances
  - Pas d’environnement d'intégration
  - Pas de contrôle de version des plugins ou thèmes personnalisés

---

### Phase 4 – 🧪 TEST

- **Ce que j’ai fait** :  
Tests manuels principalement. Quelques correctifs faits en production pour améliorer l’expérience utilisateur.

- **Ce qui était adapté** ✅ :  
  - Suivi des retours client pour corriger les bugs visuels et UX
  - Tests "live" avec le senior pour certaines fonctions

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Pas d’environnement de préproduction
  - Aucun test automatisé (unitaires, fonctionnels, etc.)
  - Pas de validation de sécurité des formulaires ou entrées utilisateur

---

### Phase 5 – 🚀 RELEASE

- **Ce que j’ai fait** :  
Mise en ligne manuelle par FTP à chaque fois que la cliente validait une modification importante.

- **Ce qui était adapté** ✅ :  
  - Communication directe avec le client pour validation

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Pas de release taguée ou versionnée
  - Pas de suivi des changements (changelog)
  - Aucun audit ou vérification finale avant mise en ligne

---

### Phase 6 – 📦 DEPLOY

- **Ce que j’ai fait** :  
Déploiement manuel via FTP directement sur l’hébergement OVH. La cliente avait la propriété du compte OVH mais l’agence gérait les accès.

- **Ce qui était adapté** ✅ :  
  - Hébergement OVH avec certificat SSL actif
  - Sauvegardes hebdomadaires et mensuelles

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Déploiements non traçables
  - Aucun rollback possible
  - Pas de séparation claire entre environnement de développement, test, production

---

### Phase 7 – ⚙️ OPERATE

- **Ce que j’ai fait** :  
La cliente utilisait le site en autonomie, et je gérais certains correctifs à la demande (bugs mineurs, ajustements).

- **Ce qui était adapté** ✅ :  
  - Suivi du bon fonctionnement via retours directs de la cliente
  - Correctifs rapides en cas de bug visuel ou d’interface

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Pas de supervision ou de logs centralisés
  - Modifications à chaud sur les fichiers de prod
  - Aucun contrôle d’intégrité ou surveillance système

---

### Phase 8 – 🔍 MONITOR

- **Ce que j’ai fait** :  
Pas de monitoring automatisé. Seuls les spams dans les formulaires ont été notés.

- **Ce qui était adapté** ✅ :  
  - Formulaire protégé par un CAPTCHA simple
  - Certificat TLS actif (HTTPS)

- **Ce que j’aurais pu améliorer** ⚠️ :  
  - Aucun système de détection d'intrusion
  - Pas de log d’accès ni d’alertes
  - Faible visibilité sur les performances ou les erreurs

---

## 🎯 Bilan général

- **Points forts de mon approche DevSecOps** :
  - Réactivité face aux bugs
  - Bonne compréhension des technos web
  - Capacité à résoudre des problèmes rapidement

- **Faiblesses identifiées** :
  - Aucune automatisation, versioning ou CI/CD
  - Manque total de culture sécurité
  - Absence de collaboration structurée et de traçabilité

- **Ce que j’ai appris** :
  - L’importance de la sécurité dès la phase de planification
  - L’utilité des environnements séparés (dev, test, prod)
  - La nécessité d’intégrer Git, des tests et des scans dans le cycle

---

## 📌 Pistes d’amélioration concrètes

1. Utiliser Git + GitHub dès le début de tout projet
2. Ajouter une CI simple avec tests, scans de plugins (via Trivy ou WPScan)
3. Mettre en place un environnement de staging pour les pré-tests
4. Automatiser les sauvegardes et surveiller les logs
5. Créer un changelog clair pour chaque release

---