# Starterkit Webflow × BYQ Supply × Claude Code

Kit de démarrage pour construire des sites **Webflow** à partir des composants **BYQ Supply**, piloté par **Claude Code** et une équipe d'agents spécialisés (UX, SEO, accessibilité, intégration).

Un dépôt = un client. Le moteur (`.claude/`) est identique d'un projet à l'autre ; seules les informations client (`.knowledge/`) changent.

## Prérequis

- [Claude Code](https://claude.com/claude-code) installé
- Connecteurs MCP actifs dans Claude :
  - **Webflow** : accès au site du client (le Designer doit être ouvert dans le navigateur pour modifier éléments et styles)
  - **BYQ Supply** : accès à la bibliothèque de composants, wireframes et gems (certains composants nécessitent un abonnement Pro)
- Un compte BYQ Supply dans le navigateur, pour le chemin de secours (copier-coller de la version Webflow native)
- Accès au **Drive partagé** du client (photos, sources lourdes, documents privés)

## Structure

```
.
├── .claude/                  ← MOTEUR (générique, ne pas modifier par client)
│   ├── CLAUDE.md             ← règles globales, format de transmission entre agents
│   ├── settings.json         ← permissions MCP (lectures autorisées, publication sur confirmation)
│   └── skills/
│       ├── onboard/          ← /onboard   : lit .knowledge et génère la fiche client
│       ├── byq/              ← /byq       : choix BYQ et reconstruction Client-First (collage BYQ en secours)
│       ├── seo/              ← /seo       : Hn, metas, OpenGraph, JSON-LD, CMS
│       ├── a11y/             ← /a11y      : audit WCAG 2.1 AA
│       ├── webflow/          ← /webflow   : exécution via le MCP Webflow
│       └── pipeline/         ← /pipeline  : BYQ → SEO → A11y → Webflow
│
├── .knowledge/               ← CLIENT (propre à chaque projet)
│   ├── client.md             ← fiche consolidée, source de vérité (générée par /onboard)
│   ├── doc/brief.md          ← brief à remplir
│   ├── charte/charte.md      ← charte à remplir
│   ├── assets/               ← logos SVG, favicon
│   ├── photos/               ← copie locale du Drive (non versionnée)
│   └── private/              ← documents sensibles (non versionnés)
│
└── .gitignore
```

## Démarrer un nouveau projet

1. **Dupliquer le kit** dans un nouveau dépôt **privé** au nom du client.
2. **Créer le dossier client** sur le Drive partagé ; noter son lien dans `.knowledge/doc/brief.md` (section *Liens*).
3. **Déposer les éléments** dans `.knowledge/` : brief, charte, logos ; photos sur le Drive puis copiées dans `photos/` ; contrats et devis dans `private/`.
4. Lancer Claude Code à la racine du projet, puis :
   ```
   /onboard
   ```
   → génère `.knowledge/client.md` et liste les informations manquantes à demander au client.
5. Construire les pages section par section :
   ```
   /pipeline hero de la page d'accueil
   ```

## Commandes

| Commande | Usage |
|---|---|
| `/onboard` | Au démarrage, et à chaque ajout de fichiers dans `.knowledge/` |
| `/pipeline` | Construire une section de bout en bout (avec points de validation) |
| `/byq` | Chercher et adapter un composant, wireframe ou gem BYQ |
| `/seo` | Auditer ou rédiger Hn, metas, données structurées |
| `/a11y` | Auditer l'accessibilité d'une section ou d'une page |
| `/webflow` | Lire ou modifier directement le site Webflow |

## Garde-fous

- **Aucune écriture sur Webflow sans validation** : chaque modification est récapitulée (avant → après) et attend votre accord.
- **Aucune publication** sans demande explicite.
- **Zéro invention** : les infos client manquantes sont signalées `[À FOURNIR : …]`, jamais inventées.
- **Confidentialité** : le contenu de `.knowledge/private/` n'est jamais recopié (ni dans `client.md`, ni sur le site).
- **Design System** : les composants BYQ sont reconstruits en classes Client-First et variables du projet. Aucune classe Tailwind n'arrive dans Webflow.

## Le cycle d'une section

1. Claude propose 2 à 3 composants BYQ (vignettes et liens) ; vous choisissez.
2. Claude réécrit le composant en HTML/CSS Client-First aux couleurs du client, avec ses textes, puis le passe en revue SEO et accessibilité.
3. Claude vous montre le récapitulatif, puis l'insère dans Webflow via le MCP après votre accord.

**Secours :** si la reconstruction coince (animations complexes, rendu trop éloigné), Claude vous propose de copier la version Webflow native depuis BYQ et de la coller dans le Designer ; il l'adapte ensuite.

## Versionnement

| Versionné dans Git ✅ | Hors Git ❌ |
|---|---|
| `.claude/`, `client.md`, `doc/`, `charte/`, `assets/` | `photos/`, `private/` et sources lourdes (`.psd`, `.ai`, `.fig`, `.tif`, vidéos, `.zip`) → **Drive partagé** |

## Reprendre un projet existant

1. Cloner le dépôt du client.
2. Ouvrir le lien Drive indiqué dans `.knowledge/client.md` → copier les photos dans `.knowledge/photos/`.
3. Lancer Claude Code : les agents lisent `client.md` et retrouvent tout le contexte (charte, mots-clés, arborescence, IDs Webflow).

## Utilisation sur claude.ai

### Claude Code sur le web (claude.ai/code) — recommandé

Le kit fonctionne tel quel : `CLAUDE.md`, skills, commandes `/xxx` et `settings.json` sont pris en compte.

- Le dépôt du client doit être sur **GitHub** (privé).
- Les connecteurs Webflow et BYQ Supply sont liés au compte claude.ai : vérifier qu'ils répondent en début de session.
- `photos/` et `private/` étant hors Git, ils sont **absents** de l'environnement cloud. `/onboard` s'appuie alors sur le lien Drive de `client.md`.
- Le Designer Webflow (avec l'app MCP) doit rester ouvert dans le navigateur, comme en local.
- Commiter et pousser `client.md` après `/onboard`, sinon il est perdu en fin de session.

### Claude.ai en mode chat (Projets) — adaptation manuelle

| Élément du kit | Équivalent sur claude.ai |
|---|---|
| `.claude/CLAUDE.md` | Coller le contenu dans les **instructions du Projet** |
| `.claude/skills/*` | Zipper chaque dossier de skill et l'importer comme **Skill** (Paramètres → Capacités). Les commandes `/xxx` ne sont plus reconnues : demander la skill par son nom (« lance l'onboarding », « audit a11y »…). |
| `.knowledge/` (brief, charte, logos) | Ajouter aux **connaissances du Projet** (jamais `private/`) |
| `client.md` | Claude produit la fiche dans la conversation ; l'ajouter soi-même aux connaissances du Projet et la tenir à jour |
| `settings.json` | **Ignoré** : seule la règle de validation de `CLAUDE.md` et les confirmations de claude.ai protègent les écritures |

## Faire évoluer le kit

Les améliorations des agents (`.claude/`) se font dans le **dépôt du starterkit**, puis sont recopiées dans les projets en cours si nécessaire. Ne jamais y ajouter d'information propre à un client.
