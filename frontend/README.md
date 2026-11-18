# TaskFlow – Frontend (Next.js + TypeScript)

Interface utilisateur de l'application de gestion de tâches **TaskFlow**, conçue selon le [Cahier des Charges Fonctionnel et Technique](file:///c:/Users/Lenovo/Gestion%20de%20taches/CAHIER%20DES%20CHARGES%20FONCTIONNEL%20ET%20TECHNIQUE.pdf) dans le cadre du projet académique de déploiement en **environnement hybride** (Cloud + Infrastructure locale).

---

## 📋 Périmètre & Fonctionnalités

### 1. Authentification & Sécurité (Section 2.1 A)
- **Inscription (`/register`)** : Nom complet, Email, Mot de passe avec confirmation.
- **Connexion (`/login`)** : Email, Mot de passe.
- **Session & Contexte (`src/context/AuthContext.tsx`)** : Gestion du jeton JWT, persistance et actualisation du profil (`/api/auth/me`).
- **Protection des routes privées** : Redirection automatique vers `/login` pour les pages non authentifiées.

### 2. Tableau de bord (`/`) (Section 2.1 C)
- 4 compteurs statistiques en temps réel :
  - **Total des tâches**
  - **Tâches à faire**
  - **Tâches en cours**
  - **Tâches terminées**
- Liste des 5 dernières tâches récentes avec accès direct aux détails.
- Raccourci pour création rapide de tâche.

### 3. Gestion complète des tâches (`/tasks`) (Section 2.1 B)
- **Création / Édition (`TaskModal`)** :
  - Titre (obligatoire)
  - Description
  - Statut (`À faire`, `En cours`, `Terminée`)
  - Priorité (`Basse`, `Moyenne`, `Haute`)
  - Date d'échéance facultative
- **Filtres & Recherche en temps réel** :
  - Recherche textuelle dans le titre et la description
  - Filtrage par statut
  - Filtrage par priorité
  - Tri par date d'échéance ou date de création
- **Changement de statut rapide** en 1 clic.
- **Suppression avec confirmation obligatoire (`DeleteConfirmModal`)** conformément à la règle de gestion #7.

### 4. Résilience & Spécificité Hybride (Exigences 3.4 & Tests T09/T10)
- **Bannière d'alerte (`ApiStatusBanner`)** : Signalement clair et immédiat à l'utilisateur lorsque le tunnel Cloudflare ou le PC local est indisponible, avec bouton de réessai.

---

## 🚀 Démarrage local

### 1. Configuration des variables d'environnement
Créez un fichier `.env.local` à la racine du dossier `frontend` :

```env
NEXT_PUBLIC_API_URL=https://taskflow-backend-k9wq.onrender.com
```
> Remplacez `http://localhost:5000` par l'URL publique de votre backend Railway lors du déploiement.

### 2. Lancer le serveur de développement
```bash
npm run dev
```

L'application est accessible sur [http://localhost:3000](http://localhost:3000).

---

## 🌐 Déploiement sur Vercel (Section 4.1 & 8)

1. Pousser le code sur votre dépôt **GitHub**.
2. Sur **Vercel** :
   - Importer le dépôt GitHub.
   - Configurer le **Root Directory** sur `frontend`.
   - Ajouter la variable d'environnement : `NEXT_PUBLIC_API_URL = <URL_DE_VOTRE_API_RAILWAY>`.
   - Cliquer sur **Deploy**.
