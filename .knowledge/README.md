# .knowledge — Base de connaissance client

Ce dossier contient **tout ce qui est propre au client**. Le reste du starterkit (`.claude/`) est générique et ne doit pas être modifié d'un projet à l'autre.

## Structure

| Dossier / fichier | Contenu | Rempli par |
|---|---|---|
| `doc/brief.md` | Brief projet : activité, cibles, objectifs, pages, mots-clés | Vous (modèle fourni) |
| `doc/` | Tout document brut : PDF, comptes rendus, contenus rédigés, anciens textes du site | Vous |
| `charte/charte.md` | Couleurs, typographies, ton, règles de marque | Vous (modèle fourni) |
| `charte/` | Charte graphique PDF, guidelines, captures | Vous |
| `assets/` | Logos (SVG de préférence), icônes, favicon | Vous |
| `photos/` | Copie locale des photos du **Drive partagé** — non versionnée | Vous |
| `private/` | Documents sensibles : contrats, devis, accès — non versionnés | Vous |
| `client.md` | **Fiche client consolidée**, source de vérité des agents | Généré par `/onboard` |

## Ce qui est versionné (Git) ou non

| Versionné ✅ | Non versionné ❌ |
|---|---|
| `client.md`, `doc/`, `charte/`, `assets/` (logos SVG légers) | `private/` : sensible, transmis par le Drive |
| | `photos/` : stockées sur le Drive partagé |
| | Sources lourdes partout (`.psd`, `.ai`, `.fig`, `.tif`, `.mov`, `.mp4`, `.zip`) |

**Reprise par un collègue :** cloner le dépôt, ouvrir le lien Drive noté dans `client.md`, copier les photos dans `photos/`. La fiche `client.md` donne immédiatement tout le contexte aux agents.

## Démarrage d'un nouveau projet
1. Créez le dossier client sur le Drive partagé et notez son lien dans `doc/brief.md` (section *Liens*).
2. Déposez les fichiers bruts dans les dossiers ci-dessus (les photos d'abord sur le Drive, puis copiées dans `photos/`).
3. Remplissez ce que vous pouvez de `doc/brief.md` et `charte/charte.md` (les champs vides sont acceptés).
4. Lancez `/onboard` : Claude lit tout, produit `client.md` et liste les informations manquantes.
5. Lancez `/pipeline` pour construire les sections.

Un exemple complet (client fictif) se trouve dans `examples/fagne-fil/`.

## Conventions de nommage
- Photos : `[page]-[sujet]-[n].jpg` (ex : `accueil-equipe-01.jpg`, `services-atelier-02.jpg`). Le nom aide à générer les alt-texts et le SEO des images.
- Logos : `logo-[variante].svg` (ex : `logo-couleur.svg`, `logo-blanc.svg`, `logo-picto.svg`).
- Poids : photos < 500 Ko, idéalement en WebP ou JPG 2000 px de large maximum.
