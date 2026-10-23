# Fiche client — Atelier Fagne & Fil

> ⚠️ CLIENT FICTIF — fiche de test du starterkit.

_Générée par /onboard le 2026-10-23 — sources : `doc/brief.md`, `doc/notes-entretien.md`, `charte/charte.md` (et `private/devis-site.md`, lu pour le contexte et non recopié)_

## Liens
- Drive partagé : [À FOURNIR]
- Site Webflow : claude-webflow-byq — **site ID : `6adb3346d883d0d4f1f1296b`** (vérifié via le MCP le 2026-10-23)
  - Page Home : `6adb3348d883d0d4f1f1297b`
  - Collections CMS : aucune pour l'instant
  - État : site vierge (0 classe, 1 collection de variables vide « Base collection »), jamais publié
  - Breakpoints : Desktop (base), Tablet ≤991, Mobile (L) ≤767, Mobile ≤479
- Responsable projet : Grégory (webdigitales)

## Identité
- **Nom :** Atelier Fagne & Fil
- **Activité :** menuiserie artisanale ; mobilier sur mesure en bois local (chêne, frêne, hêtre)
- **Fondateur :** Thomas, qui a repris en 2016 l'atelier de son oncle (source : `notes-entretien.md`)
- **Localisation :** Spa, province de Liège
- **Zone desservie :** ⚠️ contradiction, voir *Manques*
- **Coordonnées publiques :** contact@exemple-fagnefil.be ; téléphone [À FOURNIR] ; atelier visitable sur rendez-vous ; adresse [À FOURNIR]
- **Réseaux :** Instagram @fagnefil.atelier ; page Facebook (URL [À FOURNIR])

## Cibles & objectifs
- **Cible principale :** propriétaires de 35 à 60 ans qui rénovent une maison et veulent du mobilier durable (dressings, bibliothèques, cuisines)
- **Cibles secondaires :** architectes d'intérieur de la région ; gîtes et chambres d'hôtes
- **Problème :** le mobilier standard ne s'adapte pas aux maisons anciennes (murs non droits, sous-pentes)
- **Objectif n°1 :** demandes de devis qualifiées (objectif : 8 par mois)
- **CTA principal :** « Demander un devis »
- **Canaux d'acquisition actuels :** bouche-à-oreille et Instagram (source : `notes-entretien.md`)

## Offre
- **Services :** dressings et rangements sur mesure ; bibliothèques ; cuisines en bois massif ; tables de ferme ; aménagement complet de gîtes (source : `notes-entretien.md`)
- **Arguments :** bois issu de forêts de la région ; finitions à l'huile naturelle ; un seul interlocuteur du croquis à la pose ; tout est fabriqué à l'atelier
- **Processus (à mettre en avant) :** croquis → débit → assemblage → finition → pose ; délai moyen de 6 à 10 semaines
- **Preuves fournies :** 12 ans d'expérience. ⚠️ Témoignages : [À FOURNIR]
- **Citation validée par le client :** « On fait tout ici, de la planche brute au meuble fini. »
- **Prix :** **ne jamais afficher de prix** (demande du client)

## Arborescence
| Page | Objectif | Mot-clé visé | Sections pressenties |
|---|---|---|---|
| Accueil | Convaincre et amener au devis | menuisier sur mesure Spa | Hero + CTA devis ; services ; processus en 5 étapes ; réalisations à la une ; citation du fondateur ; CTA final |
| Réalisations (CMS) | Prouver par l'exemple | dressing / bibliothèque / cuisine sur mesure (par fiche) | Grille filtrable par type ; fiche projet (photos, bois, durée, lieu) |
| Savoir-faire | Rassurer sur la qualité | menuiserie artisanale Ardennes | Histoire de l'atelier ; bois locaux ; finitions ; étapes de fabrication |
| Contact / Devis | Convertir | dressing sur mesure Liège | Formulaire de devis avec envoi de photos ; zone d'intervention ; prise de rendez-vous à l'atelier |
| Gîtes & chambres d'hôtes *(proposée)* | Cible secondaire | aménagement gîte sur mesure *(déduit de `notes-entretien.md`)* | ⚠️ page souhaitée en entretien mais absente de l'arborescence du brief : à valider |

## SEO
- **Mot-clé principal :** menuisier sur mesure Spa
- **Secondaires :** dressing sur mesure Liège ; bibliothèque sur mesure ; cuisine bois massif ; menuiserie artisanale Ardennes
- **Concurrents :** [À FOURNIR]
- **JSON-LD pressenti :** `LocalBusiness` (sous-type `HomeAndConstructionBusiness`). Il manque l'adresse, le téléphone et les horaires, à compléter avant de l'écrire.

## Ton éditorial
- Chaleureux, artisanal, précis. **Jamais** luxe ni prétentieux.
- Vouvoiement ; français uniquement
- Textes **à rédiger** à partir des notes d'entretien
- Mots à employer : atelier, bois local, sur mesure, assemblage, finition naturelle *(déduit des sources)*
- À éviter : vocabulaire luxe (« prestige », « exclusif »), registre « tech »

## Design tokens
| Token | Valeur | Variable Webflow proposée |
|---|---|---|
| Primaire (Chêne fumé) | `#8A5A3B` | `--brand--primary` |
| Secondaire (Mousse des fagnes) | `#9DAF8A` | `--brand--secondary` |
| Secondaire foncé *(proposée, voir Contrastes)* | `#697C55` | `--brand--secondary-dark` |
| Texte (Écorce) | `#2B2420` | `--text--primary` |
| Fond (Lin) | `#F6F1EA` | `--background--primary` |
| Fond alternatif (Sciure) | `#E8DCCB` | `--background--secondary` |
| Succès / erreur | [À FOURNIR] | `--state--success` / `--state--error` |
| Police titres | Fraunces 500/600 (Google Fonts) | `--font--heading` |
| Police texte | Inter 400/500 (Google Fonts) | `--font--body` |
| Arrondi | 4 à 8 px | `--radius--small` (4px) / `--radius--medium` (8px) |

- **Animations :** sobres. Pas de gems très animés ; `prefers-reduced-motion` obligatoire.
- **Interdits :** pas de noir pur, pas d'effets « tech » (néons, dégradés flashy).
- **Style photo :** lumière naturelle, gros plans sur le bois et les assemblages.

## Prérequis Webflow
- [ ] Polices à installer dans *Site settings > Fonts* : Fraunces (500, 600), Inter (400, 500)
- [ ] Langue principale du site : fr

## Contrastes
| Couple | Ratio | Texte normal (4.5) | Grand texte / UI (3) |
|---|---|---|---|
| Écorce sur Lin | 13.58 | ✅ | ✅ |
| Écorce sur Sciure | 11.29 | ✅ | ✅ |
| Chêne fumé sur Lin | 5.18 | ✅ | ✅ |
| Chêne fumé sur Sciure | 4.31 | ❌ | ✅ |
| Blanc sur Chêne fumé (bouton primaire) | 5.82 | ✅ | ✅ |
| Écorce sur Mousse | 6.49 | ✅ | ✅ |
| **Blanc sur Mousse** (usage souhaité par le client) | **2.35** | ❌ | ❌ |
| Mousse sur Lin | 2.09 | ❌ | ❌ |

**Alternatives proposées :**
- Boutons verts : **blanc sur `#697C55`** (même teinte que Mousse, assombrie), ratio 4.55 ✅. Autre option : texte Écorce sur Mousse (6.49 ✅).
- Mousse `#9DAF8A` : à réserver aux éléments décoratifs (badges sans texte, illustrations), jamais pour du texte ou une icône porteuse de sens.
- Liens en Chêne fumé sur fond Sciure : seulement en grand texte, sinon Écorce.

## Médiathèque
`photos/` et `assets/` sont **vides**, et le lien du Drive manque. La médiathèque sera remplie quand les photos auront été copiées.
- Logo : le client n'a qu'un JPG basse définition ; il faut un **SVG** (couleur, blanc, picto).

## Manques & questions client
- [ ] **Lien du Drive partagé** du projet
- [ ] **Zone d'intervention :** le brief dit « rayon de 60 km autour de Spa », l'entretien dit « toute la province de Liège et un peu au-delà ». Quelle formulation retenir ?
- [ ] **Page Gîtes & chambres d'hôtes :** demandée en entretien, absente de l'arborescence. On l'ajoute ?
- [ ] **Coordonnées publiques :** téléphone, adresse de l'atelier, horaires de visite
- [ ] **Témoignages clients** (avec accord de publication)
- [ ] **Photos** des réalisations et de l'atelier (étapes de fabrication en particulier)
- [ ] **Logo vectoriel** (SVG) et ses variantes
- [ ] **Couleur des boutons verts :** valider `#697C55` ou le texte Écorce à la place du blanc sur Mousse (non conforme)
- [ ] Couleurs **succès / erreur** pour les formulaires
- [ ] **Concurrents** et **sites de référence** appréciés
- [ ] URL de la page Facebook
