---
name: pipeline
description: Exécute le workflow complet BYQ → SEO → A11y → Webflow pour créer ou refondre une section ou une page Webflow à partir de BYQ Supply. Utiliser quand l'utilisateur tape /pipeline ou demande de construire une section de bout en bout.
---

# Pipeline BYQ → SEO → A11y → Webflow

Tu enchaînes les quatre agents dans l'ordre, en endossant un seul rôle à la fois (annonce-le : `[Étape 2/4 — Agent SEO]`). Chaque étape reprend et enrichit le **Bloc de Transmission** défini dans `CLAUDE.md` ; aucune ne repart de zéro.

## 0. Cadrage
1. Lis `.knowledge/client.md`. S'il n'existe pas, ou s'il y a dans `.knowledge/` des fichiers plus récents que lui, propose de lancer `/onboard` d'abord.
2. Récupère dans la fiche la page cible, son mot-clé, les sections pressenties, les contenus et les photos disponibles.
3. Pose en une seule fois les questions sur ce qui manque encore.

## Étapes
1. **[1/4] BYQ** — suis `.claude/skills/byq/SKILL.md`. Sortie : structure Client-First + classes.
2. **[2/4] SEO** — suis `.claude/skills/seo/SKILL.md`. Sortie : Hn corrigés, metas, OG, JSON-LD.
3. **[3/4] A11y** — suis `.claude/skills/a11y/SKILL.md`. Sortie : corrections appliquées au bloc ; s'il reste des 🔴 bloquants non résolus, arrête-toi et demande comment procéder.
4. **[4/4] Webflow** — suis `.claude/skills/webflow/SKILL.md`. Présente le récapitulatif final, **attends la validation**, exécute, puis vérifie.

## Points d'arrêt
- Après l'étape 1, fais valider le choix du composant BYQ avant de poursuivre (c'est le choix le plus coûteux à défaire).
- Avant l'étape 4, validation obligatoire (règle globale).
- Jamais de publication sans demande explicite.

## Rapport final
Résumé en 5 lignes maximum : composant utilisé, page modifiée, metas posées, score a11y (bloquants restants), actions Webflow exécutées.
