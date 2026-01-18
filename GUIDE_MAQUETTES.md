# 📐 Guide des Maquettes - Agenda Pulse

## 🎯 Vue d'ensemble

Ce projet contient **8 propositions de design** pour la page d'accueil d'Agenda Pulse, organisées en 2 versions :

- **Version 1 (v1)** : 3 maquettes initiales (A, B, C)
- **Version 2 (v2)** : 5 nouvelles maquettes avec palettes différenciées

## 📁 Structure des fichiers

```
/home/ben/mes-projets/agenda-pulse-acceuil/
│
├── index-propositions-toutes.html          ← PAGE INDEX PRINCIPALE (POINT D'ENTRÉE UNIQUE)
│
├── maquette-A-classique.html               ← v1 - Maquette A
├── maquette-B-moderne.html                 ← v1 - Maquette B
├── maquette-C-editorial.html               ← v1 - Maquette C
│
├── propositions-design-2026/               ← Répertoire v2
│   ├── index.html                          ← Index des 5 nouvelles maquettes
│   ├── maquette-1-warm-professional.html
│   ├── maquette-2-nature-business.html
│   ├── maquette-3-bold-minimalist.html
│   ├── maquette-4-moderne-hybride.html
│   ├── maquette-5-tech-chaleureux.html
│   └── README.md
│
├── navigation-menu-snippet.html            ← Snippet de menu réutilisable
├── PROPOSITIONS_DESIGN.md                  ← Guide rapide
└── GUIDE_MAQUETTES.md                      ← Ce fichier

```

## 🚀 Accès rapide

### Page principale
**Ouvrir dans le navigateur :**
```
file:///home/ben/mes-projets/agenda-pulse-acceuil/index-propositions-toutes.html
```

Ou depuis le terminal :
```bash
cd /home/ben/mes-projets/agenda-pulse-acceuil
open index-propositions-toutes.html  # macOS
xdg-open index-propositions-toutes.html  # Linux
```

## 📋 Liste des maquettes

### Version 1 - Propositions Initiales

| Nom | Fichier | Palette | Cible |
|-----|---------|---------|-------|
| **A - Classique** | `maquette-A-classique.html` | Bleu #1e40af, Orange #f59e0b | Professionnels classiques |
| **B - Moderne** | `maquette-B-moderne.html` | Bleu #1e40af, Orange #f59e0b | Startups, entrepreneurs |
| **C - Editorial** | `maquette-C-editorial.html` | Bleu #1e40af, Orange #f59e0b | Créatifs, designers |

### Version 2 - Nouvelles Propositions (Janvier 2026)

| Nom | Fichier | Palette Principale | Cible |
|-----|---------|-------------------|-------|
| **1 - Warm Professional** | `propositions-design-2026/maquette-1-warm-professional.html` | Ardoise #334155, Terracotta #ea580c | Thérapeutes, consultants |
| **2 - Nature Business** | `propositions-design-2026/maquette-2-nature-business.html` | Vert Forêt #047857, Beige #d4a574 | Praticiens bien-être |
| **3 - Bold Minimalist** | `propositions-design-2026/maquette-3-bold-minimalist.html` | Noir #18181b, Jaune #eab308 | Consultants stratégie |
| **4 - Moderne Hybride** | `propositions-design-2026/maquette-4-moderne-hybride.html` | Teal #0f766e, Rose Corail #ec4899 | Professionnels tech |
| **5 - Tech Chaleureux** | `propositions-design-2026/maquette-5-tech-chaleureux.html` | Indigo #4338ca, Coral #ff6b6b | Usage quotidien |

## 🔧 Intégration du menu de navigation

Pour ajouter un menu de navigation à une maquette existante :

1. **Ouvrir** le fichier `navigation-menu-snippet.html`
2. **Copier** tout le contenu (styles + HTML)
3. **Coller** dans votre maquette juste après la balise `<body>`

Le snippet contient :
- Logo Agenda Pulse (avec image)
- Bouton "Retour à la galerie"
- Styles responsives
- Ajustement automatique du padding du body

## 🎨 Logo Agenda Pulse

**Emplacement :** `/public/lovable-uploads/671e53a0-b262-4567-b34e-0082525616b9.png`

**Utilisation dans HTML :**
```html
<img
    src="/lovable-uploads/671e53a0-b262-4567-b34e-0082525616b9.png"
    alt="Agenda Pulse Logo"
    style="width: 40px; height: 40px;"
>
```

## ➕ Ajouter une nouvelle maquette

### Architecture extensible

La structure est conçue pour faciliter l'ajout de nouvelles propositions :

1. **Créer le fichier HTML** :
   - Placer dans la racine OU dans `propositions-design-2026/`
   - Nommer avec le pattern : `maquette-X-nom-descriptif.html`

2. **Ajouter une card** dans `index-propositions-toutes.html` :

```html
<div class="maquette-card card-vX">
    <div class="card-header">
        <h3 class="card-title">Nom de la Maquette</h3>
        <p class="card-subtitle">Description courte</p>
    </div>
    <div class="card-body">
        <div class="palette-label">Palette de couleurs</div>
        <div class="palette">
            <div class="color-dot" style="background: #color1;"></div>
            <div class="color-dot" style="background: #color2;"></div>
            <!-- ... -->
        </div>
        <div class="card-meta">
            <div class="card-meta-label">Cible</div>
            <div class="card-meta-value">Description du public cible</div>
        </div>
    </div>
    <div class="card-footer">
        <a href="chemin/vers/maquette.html" class="btn-view">Voir la maquette →</a>
    </div>
</div>
```

3. **Intégrer le menu** de navigation (voir snippet ci-dessus)

## 📊 Comparaison des palettes

### Objectif des v2
Éviter les palettes mauve/lavande génériques typiques des designs IA et proposer des alternatives professionnelles, chaleureuses et adaptées.

| Maquette | Émotion | Professionnalisme | Chaleur | Usage |
|----------|---------|-------------------|---------|-------|
| Warm Professional | Raffinement | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Quotidien |
| Nature Business | Sérénité | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Prolongé |
| Bold Minimalist | Impact | ⭐⭐⭐⭐⭐ | ⭐⭐ | Intensif |
| Moderne Hybride | Dynamisme | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Moderne |
| Tech Chaleureux | Équilibre | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Universel |

## 🌐 Déploiement GitHub Pages

### URLs actuelles (à vérifier)
- **Page index** : `https://benoitcrm777.github.io/agenda-pulse-maquettes/index-propositions-toutes.html`
- **Anciennes maquettes** : `https://benoitcrm777.github.io/agenda-pulse-maquettes/maquettes.html`

### Pour mettre à jour
```bash
# Depuis le répertoire du projet
git add index-propositions-toutes.html propositions-design-2026/
git commit -m "feat: add unified design proposals index with 8 mockups"
git push origin acceuil
```

## 📝 Notes techniques

### Fonts utilisées
- **v1** : Nunito
- **v2-1 (Warm)** : Playfair Display + Nunito
- **v2-2 (Nature)** : Lora + Nunito
- **v2-3 (Bold)** : Bebas Neue + System font
- **v2-4 (Hybride)** : DM Sans
- **v2-5 (Chaleureux)** : Poppins + System font

### Responsive
Toutes les maquettes sont **mobile-first** et s'adaptent aux écrans :
- Mobile : < 768px
- Tablet : 768px - 1024px
- Desktop : > 1024px

### Animations
Toutes les maquettes utilisent des **animations CSS** (pas de JavaScript) pour :
- Transitions au hover
- Apparitions progressives (staggered)
- Micro-interactions

## 🎓 Recommandations

### Pour choisir une maquette
1. **Identifier votre public cible** (voir colonne "Cible" dans les tableaux)
2. **Tester sur plusieurs appareils** (mobile, tablet, desktop)
3. **Considérer l'usage quotidien** (fatigue visuelle, temps d'utilisation)
4. **Vérifier l'alignement avec votre marque** (professionnalisme vs chaleur)

### Prochaines étapes
1. ✅ Sélectionner 1-2 maquettes favorites
2. ✅ Tester avec des utilisateurs réels (A/B testing)
3. ✅ Adapter le contenu (remplacer les données fictives)
4. ✅ Ajouter des screenshots réels de l'application
5. ✅ Optimiser pour le SEO et la performance

## 📞 Support

**Documentation projet :** `/docs/acceuil/`
**Analyse des fonctionnalités :** `/docs/acceuil/etat-des-lieux/`

---

**Dernière mise à jour :** Janvier 2026
**Créé avec :** Claude Code + frontend-design skill
