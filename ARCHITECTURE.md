# HTX Crypto v2 - Architecture & Structure

## 🏗️ Vue d'Ensemble

HTX Crypto v2 est une plateforme de **staking et trading** construite avec **Vue.js 3** et **Vite**, optimisée pour les **Telegram Web Apps**.

```
┌─────────────────────────────────────────────────────────┐
│                   Telegram Web App                       │
│                   (telegram-web-app.js)                  │
└──────────────────────┬──────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        │              │              │
    ┌───▼────┐    ┌───▼────┐    ┌───▼────┐
    │ Vue.js │    │ Vite   │    │ Assets │
    │  Core  │    │ Bundler│    │ Loader │
    └───┬────┘    └────────┘    └────────┘
        │
    ┌───▼────────────────────────────────┐
    │   Application Modules               │
    ├─────────────────────────────────────┤
    │ • Staking Module                    │
    │ • Trading Module                    │
    │ • Wallet Integration                │
    │ • Certik Security                   │
    │ • Route Protection                  │
    └───┬────────────────────────────────┘
        │
    ┌───▼────────────────────────────────┐
    │   Analytics & Tracking              │
    ├─────────────────────────────────────┤
    │ • Kwai Analytics                    │
    │ • UWT Tracking                      │
    │ • Beacon Tracking                   │
    │ • Same.new Injection                │
    └─────────────────────────────────────┘
```

---

## 📁 Structure des Fichiers

```
htxcrypto.app/
├── index.html                          # Point d'entrée (synchronisé v2)
├── SYNC_REPORT_V2.md                   # Rapport de synchronisation
├── ASSETS_MANIFEST.json                # Manifeste des assets
├── ARCHITECTURE.md                     # Ce fichier
│
├── assets/                             # Vue.js + Vite Compiled Assets
│   ├── index-DnneLZHr.js              # Module principal (18 KB)
│   ├── index-DtYxbbHg.js              # Bundle app (1.6 MB)
│   ├── index-bJ8WzqCg.js              # Composants (1.1 MB)
│   ├── useStaking-C6BMkyt_.js         # Module staking (14 KB)
│   ├── BaseClosurePanel.vue_*.js      # Composant closure (5.6 KB)
│   ├── certik--iW1oFd7.js             # Intégration Certik (5.2 KB)
│   ├── route-block-B_A1xBdJ.js        # Route protection (27 bytes)
│   ├── default-CWwjCK04.css           # Styles par défaut (9.8 KB)
│   ├── index-C0qTE-sG.css             # Styles principaux (379 KB)
│   ├── index-CjzQ1CdB.css             # Styles additionnels (6.2 KB)
│   └── index-is9UznB4.css             # Styles complets (5.6 MB)
│
├── css2                                # Google Fonts (33 KB)
├── scevent.min.js                      # Analytics Scevent (58.5 KB)
├── uwt.js                              # Tracking UWT (55.7 KB)
├── beacon.min.js/                      # Beacon Tracking
│
├── wallet/                             # Wallet Integration
│   ├── TUTdvmr7qKA2nCMcmFrtbZZSgm5P6wetpe.jpeg
│   └── wallet.txt
│
├── api_log.json                        # API Logs
├── _next/                              # Legacy Next.js (deprecated)
└── .git/                               # Git Repository
```

---

## 🔗 Flux de Chargement

### 1. **Initialisation du DOM** (index.html)
```html
<div id="app">
  <div class="app-loading">
    <div class="spinner"></div>
  </div>
</div>
```

### 2. **Chargement des Stylesheets**
```
css2 (Google Fonts)
  ↓
assets/default-CWwjCK04.css (Reset)
  ↓
assets/index-C0qTE-sG.css (Main)
  ↓
assets/index-CjzQ1CdB.css (Addon)
  ↓
assets/index-is9UznB4.css (Complete)
```

### 3. **Chargement des Scripts (ES Modules)**
```
assets/index-DnneLZHr.js (Entry Point)
  ↓
assets/index-DtYxbbHg.js (App Bundle)
  ↓
assets/index-bJ8WzqCg.js (Components)
  ↓
assets/useStaking-C6BMkyt_.js (Staking)
  ↓
assets/BaseClosurePanel.vue_*.js (UI)
  ↓
assets/certik--iW1oFd7.js (Security)
  ↓
assets/route-block-B_A1xBdJ.js (Router)
```

### 4. **Initialisation des Services Externes**
```
Telegram Web App API
  ↓
Kwai Analytics
  ↓
UWT Tracking
  ↓
Beacon Tracking
  ↓
Same.new Injection
```

### 5. **Suppression du Loading State**
```
App Ready
  ↓
Remove .app-loading
  ↓
Display Application
```

---

## 🎯 Modules Principaux

### **1. Module Staking** 📈
**Fichier:** `assets/useStaking-C6BMkyt_.js`

Gère:
- Calcul des récompenses
- Gestion des positions de staking
- Historique des transactions
- APY/APR dynamique

```javascript
// Utilisation
import { useStaking } from './useStaking-C6BMkyt_.js'

const { 
  stake, 
  unstake, 
  rewards, 
  positions 
} = useStaking()
```

### **2. Module Wallet** 💰
**Fichier:** `wallet/`

Contient:
- Adresse de wallet (TUTdvmr7qKA2nCMcmFrtbZZSgm5P6wetpe)
- Configuration du wallet
- Images et métadonnées

### **3. Module Certik** 🔒
**Fichier:** `assets/certik--iW1oFd7.js`

Intégration:
- Vérification de sécurité
- Audit Certik
- Badge de confiance

### **4. Composant Closure Panel** 🎨
**Fichier:** `assets/BaseClosurePanel.vue_vue_type_script_setup_true_lang-Du9_Po9R.js`

Composant Vue:
- Panneau de fermeture de position
- Gestion des confirmations
- Animation de transition

### **5. Route Protection** 🛡️
**Fichier:** `assets/route-block-B_A1xBdJ.js`

Sécurité:
- Blocage des routes non autorisées
- Vérification d'authentification
- Redirection sécurisée

---

## 📊 Analytics & Tracking

### **Kwai Analytics**
```javascript
window.ka('page')           // Page view
window.ka('track', event)   // Event tracking
window.ka('identify', user) // User identification
```

### **UWT Tracking**
```javascript
window.uwt.track('page_load')
window.uwt.track('user_action')
window.uwt.track('conversion')
```

### **Beacon Tracking**
```javascript
window.beacon.track(event)
```

### **Same.new Injection**
```javascript
// Automatic injection via https://same.new/inject.js
```

---

## 🚀 Performance

### Tailles des Assets
```
CSS:        5.9 MB (volumineux)
JS:         2.8 MB (normal)
Externes:   114 KB (analytics)
─────────────────────────
Total:      8.8 MB
```

### Optimisations Appliquées
- ✅ Minification des assets
- ✅ Compression Gzip
- ✅ ES Modules (tree-shaking)
- ✅ Lazy loading des composants
- ✅ Loading state avec spinner

### Optimisations Recommandées
- 🔄 Code splitting par route
- 🔄 CSS purging (remove unused)
- 🔄 Image optimization (WebP)
- 🔄 Service Worker caching
- 🔄 Compression Brotli

---

## 🔐 Sécurité

### Telegram Web App
- ✅ Validation des données
- ✅ Signature cryptographique
- ✅ Authentification par token

### Certik Audit
- ✅ Smart contract audit
- ✅ Vulnerability scanning
- ✅ Security badge

### Route Protection
- ✅ Authentification requise
- ✅ Vérification des permissions
- ✅ Blocage des accès non autorisés

---

## 🌐 Intégrations Externes

### Telegram Bot API
```
https://telegram.org/js/telegram-web-app.js
```
- Initialisation automatique
- Expansion de la vue
- Accès aux données utilisateur

### Same.new Service
```
https://same.new/inject.js
```
- Injection de contenu
- Synchronisation cross-domain
- Service worker integration

### Analytics Services
```
scevent.min.js      → Kwai Analytics
uwt.js              → UWT Tracking
beacon.min.js       → Beacon Tracking
```

---

## 📱 Responsive Design

### Breakpoints
```
Mobile:     < 640px
Tablet:     640px - 1024px
Desktop:    > 1024px
```

### Viewport Configuration
```html
<meta name="viewport" 
      content="width=device-width, 
               initial-scale=1, 
               maximum-scale=1, 
               user-scalable=no" />
```

---

## 🔄 Flux de Données

```
User Input
    ↓
Vue Component
    ↓
Staking Module / Wallet Module
    ↓
Telegram Web App API
    ↓
Backend Server
    ↓
Blockchain (HTX Chain)
    ↓
Response
    ↓
Update UI
    ↓
Analytics Tracking
```

---

## 🛠️ Développement

### Installation Locale
```bash
# Clone le repository
git clone https://github.com/wends01/htxcrypto.app.git

# Installe les dépendances
npm install

# Lance le serveur de développement
npm run dev

# Build pour production
npm run build
```

### Structure du Projet (Vite)
```
src/
├── components/          # Composants Vue
├── pages/              # Pages de l'application
├── modules/            # Modules métier
├── utils/              # Utilitaires
├── styles/             # Stylesheets
└── main.js             # Entry point
```

---

## 📝 Versioning

### v2 (Actuelle)
- ✅ Vue.js + Vite
- ✅ Tous les modules synchronisés
- ✅ Analytics intégrés
- ✅ Telegram Web App ready

### v1 (Dépréciée)
- ❌ Next.js
- ❌ Modules déconnectés
- ❌ Chemins invalides

---

## 🐛 Troubleshooting

### Problème: Modules non chargés
**Solution:** Vérifier les chemins dans index.html
```html
<script type="module" src="assets/index-DnneLZHr.js"></script>
```

### Problème: Styles manquants
**Solution:** Vérifier l'ordre des CSS
```html
<link rel="stylesheet" href="css2" />
<link rel="stylesheet" href="assets/default-CWwjCK04.css" />
```

### Problème: Telegram API non disponible
**Solution:** Vérifier la connexion Telegram
```javascript
if (window.Telegram && window.Telegram.WebApp) {
  window.Telegram.WebApp.ready()
}
```

---

## 📚 Ressources

- [Vue.js Documentation](https://vuejs.org)
- [Vite Documentation](https://vitejs.dev)
- [Telegram Web App API](https://core.telegram.org/bots/webapps)
- [HTX Chain Documentation](https://www.htx.com)

---

## 📞 Support

Pour toute question ou problème:
1. Consultez `SYNC_REPORT_V2.md`
2. Consultez `ASSETS_MANIFEST.json`
3. Vérifiez les logs dans la console
4. Contactez l'équipe de développement

---

*Dernière mise à jour: 9 Décembre 2024*
*Version: v2*
*Status: Production Ready ✅*
