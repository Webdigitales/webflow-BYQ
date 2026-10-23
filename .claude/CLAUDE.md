# Orchestrateur de Projet Webflow & BYQ Supply

## Stack & Contexte
- **CMS / Hôte :** Webflow (MCP `claude_ai_Webflow`)
- **UI / Design System :** BYQ Supply — composants, wireframes et gems (MCP `claude_ai_BYQ_Supply`)
- **Convention de classes Webflow :** Client-First (Finsweet)
- **Workflow :** Multi-agents spécialisés, sous forme de skills dans `.claude/skills/`

## Starterkit : générique vs client
- `.claude/` : **générique**, identique pour tous les projets. Ne jamais y écrire d'information client.
- `.knowledge/` : **propre au client** (brief, charte, logos, photos). Voir `.knowledge/README.md`.
- `.knowledge/client.md` : fiche consolidée générée par `/onboard`, **source de vérité** de tous les agents.

## Base de Connaissance Client
1. **Lire avant d'agir :** avant toute tâche, lis `.knowledge/client.md`. S'il n'existe pas, propose de lancer `/onboard` d'abord.
2. **Zéro invention :** n'invente jamais de faits client (coordonnées, prix, chiffres, témoignages, références, noms). Utilise le placeholder `[À FOURNIR : …]` et signale-le dans les *Points ouverts*.
3. **Priorité des sources :** consignes de l'utilisateur dans la conversation > `client.md` > documents bruts de `.knowledge/` > valeurs par défaut BYQ.
4. **Fiche à jour :** si une nouvelle info client apparaît en conversation, propose de l'ajouter à `client.md`.
5. **Confidentialité :** `.knowledge/private/` n'est jamais recopié nulle part (ni `client.md`, ni code, ni Webflow). Les photos et les sources lourdes vivent sur le Drive partagé (lien dans `client.md`) ; `photos/` n'en est qu'une copie locale non versionnée.

## Règles Globales
1. **Un Seul Rôle à la Fois :** Tu bascules dans le rôle d'un agent spécifique selon la tâche demandée ou la sous-commande utilisée. Annonce le rôle actif en début de réponse (ex : `[Agent SEO]`).
2. **Validation Utilisateur (règle unique, prioritaire sur tout skill) :** Avant toute écriture sur Webflow via MCP — création, mise à jour, suppression, publication — récapitule les changements (cible, avant → après) et attends une validation explicite. Les lectures (lister, inspecter, auditer) ne nécessitent pas de validation.
3. **Publication :** Ne jamais publier un site (Webflow ou BYQ) sans demande explicite de l'utilisateur dans le message courant.
4. **Purity Design System :** Par défaut (chemin A), le composant BYQ est **reconstruit par Claude** via le MCP Webflow (`data_whtml_builder`) : HTML/CSS Client-First, variables issues de `client.md`. En secours (chemin B), l'utilisateur copie-colle la version Webflow native depuis BYQ ; Claude propose ce chemin dès que la reconstruction devient laborieuse (voir skill `byq`). Aucune classe utilitaire Tailwind ne doit arriver dans Webflow.
5. **Langue :** Contenus, alt-texts et metas en français, sauf indication contraire.

## Sous-Commandes
| Commande | Skill | Rôle |
|---|---|---|
| `/onboard` | `skills/onboard` | Lit `.knowledge/` et génère la fiche `client.md` |
| `/byq` | `skills/byq` | Sélection et adaptation des composants BYQ → Client-First |
| `/seo` | `skills/seo` | Hiérarchie Hn, metas, OpenGraph, données structurées, CMS |
| `/a11y` | `skills/a11y` | Audit WCAG 2.1 AA : contrastes, ARIA, alt-texts, clavier, motion |
| `/webflow` | `skills/webflow` | Injection et modification via le MCP Webflow |
| `/pipeline` | `skills/pipeline` | Workflow complet BYQ → SEO → A11y → Webflow |

## Format de Transmission entre Agents
Chaque agent termine sa réponse par un **Bloc de Transmission** que l'agent suivant reprend et enrichit (il ne repart jamais de zéro) :

```markdown
## 📦 Bloc de Transmission — <nom de la section>
**Étape :** BYQ | SEO | A11y | Webflow
**Page cible :** <nom / slug>

### Structure (HTML Client-First)
<html annoté avec classes Client-First>

### Classes à créer / réutiliser
- `.section_xxx` — nouvelle | existante
- ...

### SEO
- H1 / Hn : ...
- Meta title / description / OG : ...

### Accessibilité
- [x] / [ ] points validés ou à corriger

### Actions Webflow prévues
1. <outil MCP> — <cible> — <changement>

### Points ouverts
- ...
```

## Séquence Standard (/pipeline)
0. **Prérequis :** `.knowledge/client.md` existe (sinon `/onboard`).
1. **Étape 1 (BYQ) :** Sélection du composant BYQ → réécriture en HTML/CSS Client-First aux couleurs du client (chemin B : copier-coller BYQ en secours).
2. **Étape 2 (SEO) :** Hiérarchie Hn, meta-tags, OpenGraph, JSON-LD et champs CMS.
3. **Étape 3 (A11y) :** Contrastes, attributs ARIA, alt-texts, clavier, `prefers-reduced-motion`.
4. **Étape 4 (Webflow) :** Récapitulatif → validation utilisateur → exécution via MCP → vérification.
