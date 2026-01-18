# Décisions de Design et d'Architecture

📅 **Création** : 2026-01-17
🎯 **Objectif** : Documenter toutes les décisions importantes prises pendant le développement

---

## 🏗️ Architecture

### ADR-001 : Worktree Séparé pour la Page d'Accueil
**Date** : 2026-01-17
**Statut** : ✅ ACCEPTÉ

**Contexte** :
La page d'accueil est un feature majeur qui nécessite un développement indépendant sans impacter le travail en cours sur `main_dev_009_cpte_client`.

**Décision** :
Créer un worktree Git séparé avec sa propre branche `acceuil`.

**Conséquences** :
- ✅ Développement isolé et sans conflit
- ✅ Possibilité de travailler en parallèle sur d'autres features
- ✅ Merge facile quand prêt
- ⚠️ Nécessite de synchroniser avec la branche principale régulièrement

**Alternatives considérées** :
- Travailler directement sur `main_dev_009_cpte_client` (rejeté : risque de conflits)
- Créer une simple branche (rejeté : moins flexible pour le développement parallèle)

---

### ADR-002 : Port de Développement 8091
**Date** : 2026-01-17
**Statut** : ✅ ACCEPTÉ

**Contexte** :
Le worktree principal utilise le port 8080. Besoin d'un port différent pour éviter les conflits.

**Décision** :
Configurer Vite pour utiliser le port 8091 dans ce worktree.

**Conséquences** :
- ✅ Pas de conflit de port
- ✅ Possibilité de lancer les deux serveurs simultanément
- ✅ URL claire : http://localhost:8091/

**Implémentation** :
Modification de `vite.config.ts:121` :
```typescript
server: {
  host: "::",
  port: 8091,
}
```

---

## 🎨 Design

### ADR-003 : [À définir] Design System
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Contexte** :
Besoin de cohérence visuelle avec le reste de l'application tout en donnant une identité forte à la page d'accueil.

**Options** :
1. **Réutiliser le design system existant** (Tailwind + shadcn/ui)
   - ✅ Cohérence garantie
   - ✅ Composants déjà testés
   - ⚠️ Peut manquer de différenciation pour le landing

2. **Créer un design custom pour l'accueil**
   - ✅ Plus impactant visuellement
   - ⚠️ Risque d'incohérence
   - ⚠️ Plus de travail

**Décision** : À prendre après analyse des composants existants

---

### ADR-004 : [À définir] Stratégie d'Animation
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Options** :
1. **Framer Motion**
   - ✅ Riche en fonctionnalités
   - ✅ Facile à utiliser
   - ⚠️ Ajoute une dépendance (bundle size)

2. **CSS pur + Tailwind**
   - ✅ Pas de dépendance supplémentaire
   - ✅ Performances optimales
   - ⚠️ Moins flexible pour animations complexes

3. **Pas d'animations**
   - ✅ Simple et rapide
   - ⚠️ Moins engageant

**Décision** : À prendre lors de l'implémentation du Hero

---

## 📐 Composants

### ADR-005 : [À définir] Structure des Composants
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Options** :
1. **Composants modulaires et réutilisables**
   - ✅ Maintenabilité
   - ✅ Testabilité
   - ⚠️ Plus de fichiers

2. **Composants monolithiques par section**
   - ✅ Plus simple au départ
   - ⚠️ Moins maintenable
   - ⚠️ Difficile à tester

**Recommandation** : Option 1 (composants modulaires)

**Structure proposée** :
```
src/components/home/
  HeroSection.tsx        # Section complète
  FeaturesSection.tsx    # Section complète
  FeatureCard.tsx        # Composant réutilisable
  ...
```

---

## 🔄 Routing

### ADR-006 : [À définir] Route de la Page d'Accueil
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Contexte** :
Actuellement, l'application redirige probablement vers `/login` ou `/dashboard`. Besoin de définir comment exposer la page d'accueil.

**Options** :
1. **Remplacer la route `/` par la page d'accueil**
   - ✅ Logique pour un landing page
   - ⚠️ Peut casser le comportement actuel

2. **Créer une route `/home` ou `/landing`**
   - ✅ Pas de régression
   - ⚠️ Moins naturel pour un visiteur

3. **Logique conditionnelle sur `/`**
   - Si non authentifié → Landing page
   - Si authentifié → Dashboard
   - ✅ Meilleure UX
   - ⚠️ Plus complexe

**Décision** : À prendre après analyse du routing actuel

---

## 📊 Données

### ADR-007 : [À définir] Source des Témoignages
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Options** :
1. **Données hardcodées dans le code**
   - ✅ Simple et rapide
   - ⚠️ Pas dynamique

2. **Fichier JSON/TypeScript séparé**
   - ✅ Facile à modifier
   - ✅ Pas de base de données nécessaire

3. **Base de données (Supabase)**
   - ✅ Dynamique et administrable
   - ⚠️ Plus complexe

**Recommandation** : Option 2 pour commencer (fichier TypeScript)

---

### ADR-008 : [À définir] Données de Pricing
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Questions** :
- Quels sont les plans tarifaires d'Agenda Pulse ?
- Y a-t-il déjà un système de pricing dans le code ?
- Les prix sont-ils configurables ou fixes ?

**Décision** : Nécessite discussion avec les stakeholders

---

## 🔒 Sécurité

### ADR-009 : Réutilisation des Correctifs de Sécurité
**Date** : 2026-01-17
**Statut** : ✅ ACCEPTÉ

**Contexte** :
La branche `acceuil` est basée sur `main_dev_009_cpte_client` qui contient 5 commits de sécurité non pushés.

**Décision** :
Garder ces commits dans la branche `acceuil` pour bénéficier des correctifs de sécurité dès le départ.

**Commits inclus** :
1. `b489a521` - HSTS build verification
2. `6344c79b` - HSTS header
3. `a8767d8d` - /admin organization isolation test
4. `b21ec32f` - /admin organization isolation
5. `d5817c4c` - Centralized logger (fail-closed)

**Conséquences** :
- ✅ Sécurité renforcée dès le départ
- ✅ Conformité avec les standards du projet
- ⚠️ Ces commits devront être pushés avant de merger `acceuil`

---

## 🚀 Déploiement

### ADR-010 : [À définir] Stratégie de Merge
**Date** : À définir
**Statut** : 🔄 EN DISCUSSION

**Questions** :
- Merger `acceuil` directement dans `main` ?
- Merger dans `main_dev_009_cpte_client` d'abord ?
- Créer un PR pour review ?

**Décision** : À prendre avant la fin du développement

---

## 📝 Template pour Nouvelles Décisions

Copier ce template pour documenter une nouvelle décision :

```markdown
### ADR-XXX : [Titre de la Décision]
**Date** : YYYY-MM-DD
**Statut** : 🔄 EN DISCUSSION | ✅ ACCEPTÉ | ❌ REJETÉ | 🔄 SUPERCÉDÉ

**Contexte** :
[Pourquoi cette décision est nécessaire]

**Décision** :
[Quelle décision a été prise]

**Conséquences** :
- ✅ Avantages
- ⚠️ Inconvénients
- 🔄 Impacts

**Alternatives considérées** :
- Option A (raison de rejet)
- Option B (raison de rejet)
```

---

**Dernière mise à jour** : 2026-01-17 13:16
