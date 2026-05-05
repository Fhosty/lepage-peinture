# Site vitrine – Entreprise Lepage Fabrice, Peintre à Gien (45)

Site statique HTML/CSS/JS, sans framework, déployable sur tout hébergement web.

---

## Structure des fichiers

```
lepage-peinture/
├── index.html            → Page d'accueil
├── services.html         → Page services
├── realisations.html     → Galerie avant/après
├── a-propos.html         → Présentation de l'entreprise
├── contact.html          → Formulaire de contact & devis
├── sitemap.xml           → Plan du site pour Google
├── robots.txt            → Directives pour les robots
├── css/
│   └── style.css         → Feuille de styles (mobile-first)
├── js/
│   └── main.js           → Scripts (nav, filtres, reveal)
└── img/                  → Dossier pour toutes les photos
```

---

## Mise à jour des photos

### 1. Préparer les images

| Usage | Dimensions recommandées | Format | Poids max |
|-------|------------------------|--------|-----------|
| Galerie réalisations | 800 × 600 px | WebP ou JPEG | 150 Ko |
| Sections services | 800 × 600 px | WebP ou JPEG | 150 Ko |
| Photo de Fabrice (À propos) | 600 × 800 px | WebP ou JPEG | 120 Ko |
| Open Graph (réseaux sociaux) | 1200 × 630 px | JPEG | 200 Ko |

**Nommage conseillé :**
```
img/
├── salon-gien-avant.jpg
├── salon-gien-apres.jpg
├── facade-briare-avant.jpg
├── facade-briare-apres.jpg
├── fabrice-lepage.jpg
├── og-accueil.jpg
├── og-services.jpg
├── og-realisations.jpg
├── og-apropos.jpg
└── og-contact.jpg
```

### 2. Remplacer un placeholder dans le HTML

Cherchez les blocs `<div class="img-ph">` et remplacez-les par une balise `<img>`.

**Avant :**
```html
<div class="img-ph">
  <svg ...></svg>
  Photo à ajouter
</div>
```

**Après :**
```html
<img
  src="img/salon-gien-apres.jpg"
  alt="Peinture salon après rénovation – Gien (45)"
  loading="lazy"
  width="800"
  height="600"
>
```

> **Important :** renseignez toujours l'attribut `alt` avec une description précise incluant la ville (ex. « Gien », « Briare ») pour le SEO local.

### 3. Ajouter une réalisation dans la galerie (realisations.html)

Copiez-collez ce bloc dans `realisations.html`, à l'intérieur de `.gallery-grid` :

```html
<div class="gallery-item ba-wrap" data-category="interieur" data-reveal>
  <div class="ba-panels">
    <div class="ba-panel">
      <img src="img/NOM-avant.jpg" alt="Avant travaux – Gien" loading="lazy" width="800" height="600">
      <span class="ba-label">Avant</span>
    </div>
    <div class="ba-panel">
      <img src="img/NOM-apres.jpg" alt="Après travaux – Gien" loading="lazy" width="800" height="600">
      <span class="ba-label after">Après</span>
    </div>
  </div>
  <div class="ba-caption">
    <h3>Titre du chantier – Ville (45)</h3>
    <p>Description courte des travaux réalisés</p>
  </div>
</div>
```

**Valeurs possibles pour `data-category` :**
- `interieur` → Peinture intérieure
- `facade` → Ravalement de façade
- `decoration` → Décoration
- `renovation` → Rénovation

---

## Configurer le formulaire de contact

Le formulaire utilise **Formspree** (gratuit jusqu'à 50 envois/mois).

1. Créez un compte sur [formspree.io](https://formspree.io)
2. Créez un nouveau formulaire et copiez votre ID (ex. `xpzgkwqr`)
3. Dans `contact.html`, remplacez :
   ```html
   action="https://formspree.io/f/YOUR_FORM_ID"
   ```
   par :
   ```html
   action="https://formspree.io/f/xpzgkwqr"
   ```
4. Mettez à jour l'URL de redirection dans le champ `_next` :
   ```html
   <input type="hidden" name="_next" value="https://www.lepage-peinture.fr/contact.html?envoye=1">
   ```

### Alternative : Netlify Forms

Si vous hébergez sur Netlify, remplacez l'attribut `action` par `"#"` et ajoutez `data-netlify="true"` sur la balise `<form>`. Aucune inscription tierce nécessaire.

---

## Informations à compléter avant mise en ligne

Effectuez une recherche globale (`Ctrl+H` dans VS Code) pour remplacer ces placeholders :

| Placeholder | À remplacer par |
|-------------|-----------------|
| `06 XX XX XX XX` | Numéro de téléphone réel |
| `+33600000000` | Numéro au format international |
| `contact@lepage-peinture.fr` | Adresse email réelle |
| `[à compléter]` (SIRET) | Numéro SIRET de l'entreprise |
| `https://www.lepage-peinture.fr` | URL du vrai domaine |
| `YOUR_FORM_ID` | ID Formspree |

---

## Déploiement

### OVH / Ionos / hébergement mutualisé classique

1. Transférez tous les fichiers (sauf `README.md`) via FTP (FileZilla, Cyberduck)
2. Le dossier racine doit contenir `index.html` directement

### Netlify (recommandé, gratuit)

1. Glissez-déposez le dossier `lepage-peinture/` sur [app.netlify.com](https://app.netlify.com/drop)
2. Obtenez une URL de prévisualisation immédiate
3. Connectez ensuite votre nom de domaine dans les paramètres

### GitHub Pages

1. Créez un dépôt GitHub (public ou privé)
2. Poussez les fichiers sur la branche `main`
3. Activez GitHub Pages dans *Settings → Pages → Source : main / root*

---

## Mise à jour du sitemap

Après chaque nouvelle page ou modification importante, mettez à jour `sitemap.xml` :
- Modifiez la date `<lastmod>` au format `YYYY-MM-DD`
- Soumettez le sitemap dans **Google Search Console**

---

## Checklist avant mise en ligne

- [ ] Remplacer tous les numéros de téléphone
- [ ] Remplacer l'email
- [ ] Renseigner le SIRET dans le footer de chaque page
- [ ] Configurer l'ID Formspree dans `contact.html`
- [ ] Ajouter les vraies photos dans `img/`
- [ ] Mettre à jour le domaine dans `sitemap.xml` et les balises `og:url`
- [ ] Créer les pages `mentions-legales.html` et `politique-confidentialite.html`
- [ ] Soumettre le sitemap dans Google Search Console
- [ ] Créer / revendiquer la fiche Google Business Profile
