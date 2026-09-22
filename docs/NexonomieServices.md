Ce premier outil est conçu comme un produit autonome, que l'on pourrait appeler provisoirement **Nexonomie Services** ou **Nexonomie Reference**. Il constituerait ensuite une brique scientifique réutilisable par l'application Nexonomie complète.

L'idée centrale est de séparer très nettement **l'entité**, **le service**, **le modèle scientifique**, **le contexte local** et **la conversion économique**. Voici une spécification structurée que tu pourrais ensuite transformer en document de repository.

# Nexonomie Services

## Plateforme de référentiels, de modèles de services et de valorisation économique des entités territoriales

### 1. Objet de la plateforme

**Nexonomie Services** est une application web destinée à répertorier, documenter, calculer et valoriser économiquement les services et nuisances associés aux entités présentes dans un territoire.

L'objectif est de construire une bibliothèque de **référentiels scientifiques et économiques transparents**, permettant de passer d'une entité territoriale concrète à une estimation quantitative puis économique des services qu'elle fournit ou des nuisances qu'elle génère.

Une entité peut être par exemple :

* un arbre ;
* un groupe d'arbres ;
* une haie ;
* une forêt ;
* une mare ;
* une zone humide ;
* un parc ;
* une surface agricole ;
* une infrastructure ;
* un bâtiment ;
* une activité économique ;
* ou toute autre entité susceptible de produire un effet mesurable sur son environnement.

La plateforme doit permettre à un utilisateur de :

1. décrire une entité ;
2. la localiser géographiquement ;
3. préciser ses caractéristiques pertinentes ;
4. déterminer les services et nuisances associés ;
5. appliquer les modèles scientifiques appropriés ;
6. adapter les calculs au contexte local ;
7. convertir les résultats en valeurs économiques ;
8. consulter précisément la chaîne de calcul et les sources utilisées.

L'objectif n'est donc pas simplement de fournir une valeur en euros, mais de rendre cette valeur **explicable, traçable, documentée et reproductible**.

---

# 2. Principe général

Le fonctionnement général peut être représenté par la chaîne suivante :

```text
                    ENTITÉ
                       │
          ┌────────────┴────────────┐
          │                         │
    Caractéristiques            Localisation
          │                         │
          └────────────┬────────────┘
                       │
                 CONTEXTE LOCAL
                       │
                       ▼
             RÉFÉRENTIELS DE SERVICES
                       │
              ┌────────┴────────┐
              │                 │
        Services positifs   Effets négatifs
              │                 │
              └────────┬────────┘
                       │
                       ▼
                MODÈLE SCIENTIFIQUE
                       │
                       ▼
                GRANDEUR PHYSIQUE
                       │
                       ▼
              CONVERSION ÉCONOMIQUE
                       │
                       ▼
                 €/an ou €/unité
```

Cette architecture doit rester générique.

Un service peut être calculé directement à partir de l'entité, ou nécessiter un modèle intermédiaire décrivant son influence sur une population ou un territoire.

---

# 3. Deux catégories fondamentales : bénéfices et nuisances

La plateforme ne doit pas être limitée aux services écosystémiques positifs.

Elle doit pouvoir représenter deux grandes catégories.

## 3.1 Services ou bénéfices

Exemples :

* régulation thermique ;
* stockage du carbone ;
* séquestration du carbone ;
* purification de l'air ;
* rétention de l'eau ;
* limitation du ruissellement ;
* protection contre les inondations ;
* réduction du bruit ;
* biodiversité ;
* pollinisation ;
* production agricole ;
* loisirs ;
* bien-être ;
* amélioration de la qualité de vie.

## 3.2 Nuisances ou coûts

Exemples :

* pollution atmosphérique ;
* émissions de particules ;
* bruit ;
* consommation d'eau ;
* émissions de carbone ;
* risques sanitaires ;
* congestion ;
* dégradation d'un habitat ;
* coûts d'entretien ;
* nuisances olfactives.

Le système doit donc utiliser une notion générique de **Service/Effect**, avec une polarité éventuelle :

```text
POSITIVE
NEGATIVE
NEUTRAL
```

Il ne faut pas présupposer que tout service est bénéfique.

---

# 4. L'entité comme point de départ

L'utilisateur commence par décrire une entité.

## Exemple : un arbre

L'application peut demander :

```text
Type :
Arbre

Espèce :
Quercus robur

Localisation :
Lille, France

Hauteur :
18 m

Diamètre du tronc :
45 cm

Diamètre du houppier :
12 m

Âge estimé :
40 ans

État :
Bon

Surface foliaire :
[optionnel]

Irrigation :
Naturelle
```

Toutes les variables ne sont pas nécessairement disponibles.

L'application doit donc distinguer :

* valeur connue ;
* valeur inconnue ;
* valeur estimée ;
* valeur par défaut ;
* valeur calculée.

Une donnée absente ne doit jamais être automatiquement interprétée comme zéro.

---

# 5. Localisation et contexte territorial

La localisation est une composante essentielle du calcul.

Deux entités identiques physiquement peuvent avoir des valeurs économiques différentes selon leur contexte.

Par exemple, la valeur d'une économie de climatisation dépend notamment :

* du climat ;
* des températures ;
* du nombre de jours chauds ;
* du prix de l'électricité ;
* du type de bâtiments environnants ;
* éventuellement du mix énergétique.

La localisation peut donc être représentée par :

```text
Entité
   │
   ├── coordonnées
   │
   ├── commune
   ├── département
   ├── région
   └── pays
```

et alimenter automatiquement des paramètres contextuels.

Exemple :

```text
Prix de l'électricité
→ référentiel national/régional

Température moyenne
→ données climatiques locales

Population concernée
→ données démographiques locales

Coût moyen d'un arrêt maladie
→ données économiques/sanitaires
```

Le système doit conserver la source et la date de chaque donnée contextuelle.

---

# 6. Les référentiels de services

Le cœur de la plateforme est constitué d'un catalogue de référentiels.

Chaque référentiel décrit un service ou un effet ainsi que la manière de le calculer.

Une **tuile de service** peut par exemple afficher :

```text
┌───────────────────────────────────────┐
│ 🌳 RÉGULATION THERMIQUE              │
│                                       │
│ Type       Service écosystémique      │
│ Polarité   Positive                   │
│                                       │
│ Entités    Arbre, forêt, parc         │
│                                       │
│ Résultat   kWh/an                     │
│ Valeur     €/an                       │
│                                       │
│ Sources    INRAE · ADEME · littérature│
│                                       │
│ Méthode    Modèle scientifique        │
│ Version    1.2                        │
│                                       │
│ [Voir le modèle] [Calculer]           │
└───────────────────────────────────────┘
```

La tuile doit fournir suffisamment d'information pour comprendre rapidement le service, mais permettre d'ouvrir une fiche beaucoup plus détaillée.

---

# 7. Fiche détaillée d'un service

Chaque référentiel doit posséder une page documentée.

Elle contient au minimum :

### Identification

* nom ;
* description ;
* catégorie ;
* polarité ;
* types d'entités compatibles.

### Entrées

Liste des paramètres nécessaires.

Exemple :

```text
Espèce
Hauteur
Diamètre du houppier
Âge
Localisation
```

### Modèle

Description de la formule ou méthode utilisée.

### Sortie

Exemple :

```text
kWh/an
kg CO₂/an
m³ d'eau/an
jours d'arrêt évités/an
€/an
```

### Conversion économique

Description de la transformation vers une valeur monétaire.

### Sources

* publications scientifiques ;
* INRAE ;
* ADEME ;
* organismes publics ;
* bases internationales ;
* études locales ;
* autres références documentées.

### Hypothèses

Toutes les hypothèses utilisées doivent être explicites.

### Domaine de validité

Le référentiel doit indiquer dans quelles conditions son utilisation est pertinente.

---

# 8. Exemple 1 — Régulation thermique d'un arbre

Prenons un arbre situé à Lille.

L'utilisateur fournit :

```text
Espèce : Quercus robur
Hauteur : 18 m
Houppier : 12 m
Localisation : Lille
```

Le référentiel peut utiliser ces informations pour estimer une quantité physique de refroidissement.

Conceptuellement :

```text
Caractéristiques de l'arbre
        ↓
Surface foliaire estimée
        ↓
Effet thermique
        ↓
Puissance de refroidissement équivalente
        ↓
Énergie économisée sur une année
        ↓
kWh/an
        ↓
Prix local de l'électricité
        ↓
€/an
```

La plateforme pourrait afficher :

```text
Régulation thermique

Effet estimé :
X kWh/an

Équivalent énergétique :
Y kWh/an

Prix de référence :
Z €/kWh

Valeur économique :
X × Z = W €/an
```

Les valeurs numériques ci-dessus sont illustratives : le système réel doit les calculer exclusivement à partir d'un modèle documenté et de paramètres sourcés.

---

# 9. Conversion économique par chaîne de traduction

La conversion en euros ne doit pas nécessairement être directe.

Le système doit pouvoir représenter des **pipelines de conversion**.

Par exemple :

```text
Arbre
 ↓
surface foliaire
 ↓
effet de refroidissement
 ↓
puissance thermique équivalente
 ↓
heures annuelles
 ↓
énergie économisée
 ↓
kWh
 ↓
prix du kWh
 ↓
€/an
```

Chaque flèche correspond à une règle, une formule ou un coefficient.

L'utilisateur doit pouvoir ouvrir chaque étape.

Par exemple :

```text
Énergie économisée
= puissance équivalente × durée d'utilisation
```

puis :

```text
Valeur économique
= énergie économisée × prix de référence
```

Cette architecture est fondamentale : **le résultat final n'est jamais une boîte noire**.

---

# 10. Exemple 2 — Stockage du carbone

Pour un arbre ou une forêt, un autre référentiel peut estimer le stockage du carbone.

Une chaîne possible serait :

```text
Espèce
+
diamètre
+
hauteur
+
âge
+
biomasse estimée
        ↓
carbone stocké
        ↓
CO₂ équivalent
        ↓
valorisation du carbone
        ↓
€/an ou valeur patrimoniale
```

Il faudra ici distinguer plusieurs notions qui ne doivent pas être confondues :

* stock de carbone ;
* séquestration annuelle ;
* émissions évitées ;
* valeur annuelle ;
* valeur du stock.

La plateforme doit préserver cette distinction.

---

# 11. Exemple 3 — Rétention de l'eau

Pour une mare ou une zone humide :

```text
Surface
+
profondeur
+
type de sol
+
pluviométrie locale
        ↓
capacité de rétention
        ↓
volume d'eau retenu
        ↓
réduction du ruissellement
        ↓
coût évité d'infrastructure hydraulique
        ↓
€/an
```

La localisation intervient directement dans le calcul via :

* pluviométrie ;
* caractéristiques hydrologiques ;
* prix des infrastructures ;
* fréquence des événements extrêmes.

Le référentiel doit donc pouvoir appeler des paramètres géographiques externes.

---

# 12. Exemple 4 — Effets sanitaires diffus

Certains effets ne peuvent pas être calculés directement à partir de l'entité.

Prenons la purification de l'air par les arbres.

On peut avoir une chaîne conceptuelle telle que :

```text
Arbre
 ↓
réduction de certains polluants
 ↓
concentration moyenne de pollution
 ↓
exposition de la population
 ↓
variation du risque sanitaire
 ↓
nombre d'événements évités
 ↓
coût médical évité
+
coût économique de l'absentéisme évité
 ↓
€/an
```

Ce type de calcul est beaucoup plus diffus.

L'effet d'un arbre ne concerne pas nécessairement uniquement les personnes situées immédiatement à côté de celui-ci.

Il peut dépendre :

* de la population exposée ;
* de la météorologie ;
* de la structure urbaine ;
* des concentrations initiales ;
* des caractéristiques de l'entité ;
* de la distribution des populations ;
* des relations dose-réponse disponibles dans la littérature.

Le référentiel doit donc pouvoir représenter des modèles territoriaux.

---

# 13. Référentiels statistiques et régression

Certains modèles pourront être construits à partir de données agrégées.

Par exemple, supposons que l'on dispose pour plusieurs villes :

```text
Ville
Population
Nombre d'arbres
Surface végétalisée
Concentration de particules
Nombre de cas d'asthme
Jours d'arrêt maladie
Dépenses médicales
...
```

Une analyse statistique peut chercher à estimer une relation entre certaines caractéristiques environnementales et certains indicateurs sanitaires.

Conceptuellement :

```text
Données de plusieurs territoires
              ↓
      modèle statistique
              ↓
   effet marginal estimé
              ↓
      par entité / unité
              ↓
     adaptation locale
              ↓
       coût estimé
```

La plateforme pourrait alors proposer un référentiel de type :

> **Effet sanitaire associé à la présence d'arbres en milieu urbain**

avec :

* population de référence ;
* variables utilisées ;
* méthode statistique ;
* coefficient(s) estimé(s) ;
* intervalles d'incertitude ;
* population et territoires utilisés pour l'estimation ;
* limites d'interprétation ;
* sources des données.

---

# 14. Attention particulière aux modèles statistiques

Les modèles statistiques doivent être présentés comme tels.

La plateforme doit distinguer :

```text
Mesure directe
Relation physique
Modèle mécaniste
Relation empirique
Régression statistique
Hypothèse
Approximation
```

Une association statistique observée entre deux variables ne doit pas être automatiquement présentée comme une relation causale.

La fiche du référentiel doit donc préciser le statut scientifique du modèle.

---

# 15. Adaptation au contexte local

Un même référentiel peut utiliser des paramètres différents selon la localisation.

Par exemple :

```text
                    RÉFÉRENTIEL
                         │
             ┌───────────┴───────────┐
             │                       │
       Modèle général          Paramètres locaux
                                     │
                    ┌────────────────┼───────────────┐
                    │                │               │
                 climat        prix énergie      population
```

L'utilisateur indique simplement :

```text
Localisation : Lille
```

et l'application recherche automatiquement les paramètres contextuels pertinents.

Le système doit afficher les paramètres effectivement utilisés.

---

# 16. Entités multiples

Le système doit pouvoir traiter une entité composée.

Exemple :

```text
Forêt
 ├── 350 chênes
 ├── 120 bouleaux
 ├── 80 hêtres
 └── ...
```

Deux approches peuvent être utilisées :

### Approche agrégée

L'utilisateur décrit directement :

```text
Surface : 12 ha
Composition : ...
Densité : ...
```

Le référentiel calcule directement les services.

### Approche décomposée

La forêt est représentée comme un ensemble d'entités :

```text
Forest
   ├── Tree 1
   ├── Tree 2
   ├── Tree 3
   └── ...
```

Le système agrège ensuite les contributions.

La plateforme doit supporter les deux approches.

---

# 17. Agrégation

L'agrégation doit être contrôlée.

Si une forêt contient 1 000 arbres, il ne faut pas nécessairement calculer :

```text
valeur forêt = 1 000 × valeur arbre
```

Certains services présentent :

* des effets non linéaires ;
* des effets de seuil ;
* des interactions ;
* des effets dépendant de la densité ;
* des effets territoriaux.

Le référentiel doit donc indiquer si l'agrégation est :

```text
LINEAR
NON_LINEAR
INTERACTIVE
TERRITORIAL
UNKNOWN
```

et fournir la méthode correspondante.

---

# 18. Services positifs et négatifs sur une même entité

Une même entité peut produire simultanément plusieurs effets de signe différent.

Par exemple, un arbre peut :

```text
+ réguler la température
+ stocker du carbone
+ filtrer certains polluants
+ contribuer à la biodiversité
+ améliorer le bien-être

mais éventuellement :

- produire certains coûts d'entretien
- augmenter certains risques dans des contextes spécifiques
```

L'application doit donc afficher les services individuellement.

Elle ne doit pas immédiatement produire uniquement un « score global ».

---

# 19. Tableau de synthèse d'une entité

Après calcul, l'utilisateur pourrait obtenir une vue telle que :

```text
╔══════════════════════════════════════════════════╗
║              ARBRE — Quercus robur              ║
║              Lille · 18 m · 12 m houppier       ║
╠══════════════════════════════════════════════════╣
║                                                  ║
║  SERVICES POSITIFS                              ║
║                                                  ║
║  🌡 Régulation thermique       + XXX €/an        ║
║  🌫 Purification de l'air     + XXX €/an        ║
║  💧 Régulation de l'eau       + XXX €/an        ║
║  🌳 Stockage carbone          + XXX €/an        ║
║  🧠 Bien-être                 + XXX €/an        ║
║                                                  ║
║  EFFETS NÉGATIFS                                ║
║                                                  ║
║  🔧 Entretien                 - XXX €/an        ║
║                                                  ║
║  ──────────────────────────────────────────────  ║
║                                                  ║
║  Valeur calculée selon les référentiels actifs  ║
║                                                  ║
║  [Explorer les calculs] [Voir les sources]      ║
╚══════════════════════════════════════════════════╝
```

Le total éventuel ne doit être présenté qu'avec les précautions méthodologiques nécessaires.

---

# 20. Transparence du calcul

Pour chaque résultat, l'utilisateur doit pouvoir ouvrir :

```text
Résultat
   ↓
Service
   ↓
Modèle
   ↓
Paramètres utilisés
   ↓
Données de l'entité
   ↓
Paramètres locaux
   ↓
Formules
   ↓
Sources
```

Exemple :

```text
Valeur de régulation thermique
= 184 €/an

Détails :

Houppier
12 m

Surface estimée
113 m²

Modèle thermique
REF-TREE-COOLING-1.2

Puissance équivalente
...

Durée annuelle
...

Prix électricité
...

Source prix
...

Référence scientifique
...
```

L'utilisateur doit pouvoir comprendre comment le résultat a été obtenu sans devoir consulter le code informatique.

---

# 21. Catalogue des référentiels

Le site doit également fonctionner comme une bibliothèque scientifique.

Une page catalogue permet de rechercher :

```text
Tous les services
```

avec filtres :

* catégorie ;
* entité compatible ;
* positif/négatif ;
* environnement ;
* santé ;
* économie ;
* climat ;
* eau ;
* biodiversité ;
* niveau de preuve ;
* localisation ;
* disponibilité des données.

Chaque référentiel possède une fiche détaillée.

---

# 22. Gestion des versions

Un référentiel scientifique doit être versionné.

Par exemple :

```text
Thermal regulation of trees
Version 1.0
Version 1.1
Version 2.0
```

Une modification du modèle ou d'un paramètre ne doit pas rendre impossible la compréhension d'une analyse passée.

Chaque calcul doit donc enregistrer :

```text
service_id
model_version
parameter_versions
context_data_versions
calculation_date
```

---

# 23. Sources et bibliographie

Les sources doivent être des objets structurés.

Une source peut être :

* publication scientifique ;
* rapport INRAE ;
* référentiel ADEME ;
* données publiques ;
* rapport gouvernemental ;
* base internationale ;
* étude locale ;
* analyse statistique interne.

Chaque source devrait comporter :

```text
Auteur(s)
Titre
Année
Organisme / journal
DOI ou identifiant
URL
Description
Portée
```

Les résultats doivent pouvoir être reliés directement aux sources utilisées.

---

# 24. Interface d'administration scientifique

Une interface spécifique pourra permettre à des experts de créer ou modifier les référentiels.

Elle devra permettre de définir :

```text
Service
   ↓
Inputs
   ↓
Formules
   ↓
Paramètres
   ↓
Sources
   ↓
Conversions
   ↓
Outputs
```

Les référentiels peuvent passer par des états :

```text
DRAFT
UNDER_REVIEW
VALIDATED
DEPRECATED
```

Un référentiel non validé ne doit pas être présenté comme une connaissance scientifique établie.

---

# 25. Architecture conceptuelle du calcul

Le moteur de calcul peut être conçu comme un système de pipelines.

Par exemple :

```text
Entity
   │
   ▼
Input extraction
   │
   ▼
Context enrichment
   │
   ▼
Service model
   │
   ▼
Physical / statistical effect
   │
   ▼
Economic conversion
   │
   ▼
Valuation
```

Chaque étape doit être indépendante et documentée.

Cela permettra ultérieurement de réutiliser exactement les mêmes modèles dans l'application Nexonomie complète.

---

# 26. Interface utilisateur principale

L'application pourrait être organisée autour de quatre espaces.

### 1. Catalogue

Explorer tous les services et référentiels.

### 2. Calculateur

Décrire une entité et calculer ses services.

### 3. Résultats

Explorer les valeurs calculées et leur décomposition.

### 4. Référentiels

Pour les utilisateurs experts : créer, documenter, versionner et valider les modèles.

---

# 27. Exemple complet de parcours utilisateur

Un utilisateur souhaite analyser un arbre.

### Étape 1 — Entité

Il sélectionne :

> Arbre

### Étape 2 — Caractéristiques

Il renseigne :

> Quercus robur, 18 m, houppier 12 m, 40 ans.

### Étape 3 — Localisation

Il indique :

> Lille.

L'application récupère automatiquement les paramètres contextuels disponibles.

### Étape 4 — Services disponibles

L'application identifie les référentiels applicables :

```text
✓ Régulation thermique
✓ Stockage carbone
✓ Séquestration carbone
✓ Purification de l'air
✓ Régulation de l'eau
✓ Biodiversité
✓ Bien-être
...
```

### Étape 5 — Calcul

Chaque service est calculé indépendamment.

### Étape 6 — Valorisation

Les résultats sont convertis selon les pipelines disponibles.

### Étape 7 — Exploration

L'utilisateur obtient :

```text
Régulation thermique       XXX €/an
Stockage carbone           XXX €/an
Purification de l'air     XXX €/an
...
```

### Étape 8 — Audit

Il peut ouvrir chaque résultat pour consulter :

* les paramètres ;
* les formules ;
* les hypothèses ;
* les sources ;
* les données locales ;
* la version du modèle.

---

# 28. Relation avec l'application Nexonomie complète

Cette plateforme doit être conçue comme une **brique autonome**, mais avec une architecture compatible avec la future application Nexonomie.

À terme :

```text
                NEXONOMIE
                    │
        ┌───────────┴───────────┐
        │                       │
   Territoire              Services
        │                       │
      Assets              Référentiels
        │                       │
        └───────────┬───────────┘
                    │
              Dépendances
                    │
               Propagation
                    │
              Nexonomic cost
```

L'outil actuel constitue donc le futur **moteur de services et de valorisation**.

Il doit être possible, plus tard, pour Nexonomie de demander :

```text
CalculateServices(
    entity,
    location,
    parameters,
    reference_versions
)
```

et de recevoir une réponse structurée :

```text
[
  {
    service: "thermal_regulation",
    quantity: ...,
    unit: "...",
    annual_value: ...,
    confidence: ...,
    model_version: "...",
    sources: [...]
  },
  ...
]
```

Cette séparation permettra de développer et valider le moteur scientifique indépendamment de l'application cartographique et du graphe nexonomique.

---

# 29. Principes scientifiques fondamentaux

La plateforme doit respecter les principes suivants.

### Traçabilité

Aucune valeur économique ne doit apparaître sans possibilité de remonter jusqu'à son modèle et ses sources.

### Transparence

Les formules et conversions doivent être lisibles.

### Localisation

Les paramètres dépendant du territoire doivent être explicitement identifiés.

### Incertitude

Lorsque les données scientifiques permettent d'estimer une incertitude, celle-ci doit être conservée.

### Distinction causalité / corrélation

Une relation statistique ne doit pas être présentée comme une relation causale sans justification.

### Pas d'invention

Lorsqu'un coefficient scientifique manque, le système doit signaler l'information manquante plutôt que l'inventer.

### Versionnement

Un calcul doit toujours pouvoir être relié à la version précise du référentiel utilisé.

### Pas de double comptage

Deux services apparemment distincts peuvent représenter le même effet sous-jacent. Le système doit donc conserver leur indépendance conceptuelle sans supposer que leurs valeurs peuvent nécessairement être additionnées.

---

# 30. Objectif du premier prototype

Le premier prototype n'a pas besoin d'implémenter immédiatement des centaines de référentiels.

Il devrait démontrer la chaîne complète sur quelques cas bien documentés :

1. **Arbre → régulation thermique → €/an**
2. **Arbre → carbone → €/an**
3. **Mare → rétention d'eau → €/an**
4. **Arbre → purification de l'air → effet sanitaire → €/an**
5. **Forêt → agrégation de services**

Le prototype devra surtout démontrer que le système sait :

> **décrire une entité → la contextualiser → sélectionner les services applicables → exécuter leurs pipelines → produire une valeur économique → expliquer entièrement cette valeur.**

La richesse du catalogue pourra ensuite croître progressivement sans modifier l'architecture fondamentale.
