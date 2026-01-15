# 🚀 GUIDE DE DÉPLOIEMENT - DEVOIR PSE V3

## Prérequis
- Compte GitHub
- Fichiers du projet téléchargés

---

## DÉPLOIEMENT EN 5 MINUTES

### 1️⃣ Créer le dépôt GitHub

1. Aller sur https://github.com/new
2. **Configurer** :
   ```
   Repository name : devoir-pse-aepe-v3
   Description     : CAP AEPE - Devoir PSE V3 Professionnel
   Visibilité      : ✅ Public
   Initialize      : ❌ Ne rien cocher
   ```
3. Cliquer sur **"Create repository"**

---

### 2️⃣ Uploader les fichiers

**Méthode simple (glisser-déposer)** :

1. Dans le dépôt vide, cliquer sur **"uploading an existing file"**
2. Glisser-déposer les 3 fichiers :
   - `index.html` ⭐
   - `README.md`
   - `.gitignore`
3. Commit message : `Initial commit - Devoir PSE V3 Professionnel`
4. Cliquer sur **"Commit changes"**

---

### 3️⃣ Activer GitHub Pages

1. Aller dans **Settings** (⚙️)
2. Menu latéral : cliquer sur **"Pages"**
3. Configurer :
   ```
   Source : Deploy from a branch
   Branch : main
   Folder : / (root)
   ```
4. Cliquer sur **"Save"**
5. Attendre 2-3 minutes

---

### 4️⃣ Vérifier le déploiement

**URL de votre site** :
```
https://[votre-username].github.io/devoir-pse-aepe-v3/
```

**Tests à effectuer** :
- ✅ Page d'accueil s'affiche
- ✅ Consignes accessibles
- ✅ Cartouche verrouillable
- ✅ Questions navigables avec filtres
- ✅ Correction fonctionnelle
- ✅ Email généré correctement
- ✅ Responsive (tester sur mobile)

---

### 5️⃣ Partager aux stagiaires

**Lien à communiquer** :
```
https://[votre-username].github.io/devoir-pse-aepe-v3/
```

**Accompagnement suggéré** :
- Présenter la démarche PSE (Observer → Analyser → Agir)
- Expliquer les modes Devoir vs Entraînement
- Préciser les critères d'évaluation
- Montrer un exemple de bonne réponse

---

## MÉTHODE ALTERNATIVE : GIT EN LIGNE DE COMMANDE

Si vous préférez Git :

```bash
# 1. Cloner le dépôt
git clone https://github.com/[username]/devoir-pse-aepe-v3.git
cd devoir-pse-aepe-v3

# 2. Ajouter les fichiers
cp /chemin/vers/index.html .
cp /chemin/vers/README.md .
cp /chemin/vers/.gitignore .

# 3. Commit
git add .
git commit -m "Initial commit - Devoir PSE V3 Professionnel"

# 4. Push
git push origin main
```

---

## MISE À JOUR DU CONTENU

### Modifier une question

1. **Via GitHub** :
   - Ouvrir `index.html`
   - Cliquer sur ✏️ (Edit)
   - Rechercher la question (Ctrl+F : `id:"q...`)
   - Modifier le texte
   - Commit changes

2. **Via Git** :
   ```bash
   # Éditer localement
   nano index.html
   
   # Commit et push
   git add index.html
   git commit -m "Mise à jour question 5"
   git push
   ```

### Ajouter une nouvelle question

**Structure à suivre** :
```javascript
{
  id: "q27",                    // ID unique
  type: "mcq",                  // mcq, msq, ou short
  points: 1.5,                  // Barème
  theme: "sst",                 // Thème pour filtres
  tags: ["risk","pro"],         // Tags d'affichage
  title: "Titre court",
  subtitle: "Sous-titre pédagogique",
  scenario: "Contexte détaillé...",
  prompt: "Question précise ?",
  choices: [                    // Pour QCM uniquement
    {key:"A", a:"Réponse A"},
    {key:"B", a:"Réponse B"},
    // ...
  ],
  answer: ["B"],               // Clés correctes
  rationale: "Explication...", // Justification
  image: "data:image/svg..."   // SVG optionnel
}
```

---

## PERSONNALISATION

### Modifier l'email formateur

**Ligne 281** dans `index.html` :
```html
<input id="emailFormateur" type="email" value="benoit.deflandre@ac-nice.fr" />
```
Remplacer par votre email.

### Modifier le logo

**Ligne 174-177** : personnaliser le SVG ou remplacer par une image.

### Adapter les couleurs

**Lignes 9-22** : modifier les valeurs CSS dans `:root`.

---

## DÉPANNAGE

### ❌ Le site ne s'affiche pas

**Causes possibles** :
1. GitHub Pages pas activé → Vérifier Settings > Pages
2. Mauvaise branche sélectionnée → Doit être `main`
3. Fichier mal nommé → Doit être exactement `index.html`
4. Délai de déploiement → Attendre 2-3 minutes

**Solution** :
- Vérifier l'onglet **Actions** (workflows de déploiement)
- Vérifier le nom du fichier (sensible à la casse)
- Forcer un nouveau commit pour relancer le build

### ❌ Les questions ne s'affichent pas

**Causes** :
- Erreur JavaScript (syntaxe dans le tableau QUESTIONS)
- Console navigateur : F12 > Console (voir erreurs)

**Solution** :
- Valider le JavaScript avec un linter
- Vérifier les virgules et accolades
- Tester localement en ouvrant `index.html` dans un navigateur

### ❌ L'email ne se génère pas

**Causes** :
- Aucun client email configuré sur l'appareil
- Navigateur bloque `mailto:`

**Solution** :
- Utiliser le bouton **"Copier"** à la place
- Configurer un client email (Outlook, Thunderbird, Mail)
- Ou copier manuellement le texte des résultats

### ❌ Mode responsive cassé

**Causes** :
- Cache navigateur
- CSS non chargé

**Solution** :
- Vider le cache (Ctrl+Shift+R)
- Tester en navigation privée
- Vérifier la balise `<meta name="viewport"...>`

---

## STATISTIQUES & SUIVI

### Activer Google Analytics (optionnel)

Ajouter avant `</head>` :
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Alternative respectueuse de la vie privée

**Plausible Analytics** ou **Matomo** (auto-hébergé)

---

## SÉCURITÉ & CONFIDENTIALITÉ

### ✅ Points positifs
- Pas de base de données → Aucune donnée stockée en ligne
- Réponses locales uniquement
- Email via client local (sécurisé)
- Pas de tracking par défaut

### ⚠️ Points d'attention
- Dépôt public → code source visible (normal)
- Pas d'authentification (accès libre)
- Pas de limite de tentatives

### Recommandations
- Ne PAS inclure de données sensibles dans le code
- Informer les stagiaires que le site est public
- Pour un usage confidentiel, héberger en interne

---

## ARCHIVAGE & BACKUP

### Sauvegarder localement
```bash
# Cloner le dépôt complet
git clone https://github.com/[username]/devoir-pse-aepe-v3.git

# Créer une archive ZIP
zip -r devoir-pse-v3-backup.zip devoir-pse-aepe-v3/
```

### Versioning
- GitHub conserve tout l'historique
- Possibilité de revenir en arrière (commits)
- Utiliser les tags pour marquer les versions importantes

---

## ÉVOLUTIONS FUTURES

### Fonctionnalités envisageables
- [ ] Export PDF des résultats
- [ ] Mode révision avec flashcards
- [ ] Statistiques de progression
- [ ] Timer pour mode examen
- [ ] Sauvegarde locale des brouillons

### Maintenance
- Relire et actualiser les questions chaque année
- Adapter selon retours stagiaires
- Mettre à jour selon évolutions réglementaires

---

## SUPPORT TECHNIQUE

**Concepteur** : Benoît DEFLANDRE  
**Email** : benoit.deflandre@ac-nice.fr  

**Documentation GitHub Pages** : https://docs.github.com/pages  
**Forum d'entraide** : GitHub Community

---

**Version du guide** : 1.0  
**Dernière mise à jour** : Janvier 2025
