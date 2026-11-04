# Plan d'action

Légende : `[ ]` à faire · `[~]` en cours · `[x]` fait · `[?]` bloqué (voir QUESTIONS.md)

## Choix techniques
<!-- Proposés puis validés par l'utilisateur ; chaque choix avec sa raison en quelques mots. -->
- Langage / cadre : …
- Interface : …
- Stockage : …
- Déploiement : …
- Tests : … (avec des services simulés pour ne pas dépendre des vrais serveurs)

## Phase 0 — Socle
- [ ] Structure du projet
- [ ] Configuration (fichier `.env`, jamais committé ; `.env.exemple` documenté)
- [ ] Tests automatiques + intégration continue (à chaque envoi sur GitHub)
- [ ] Fichiers de déploiement adaptés à la machine cible

## Phase 1 — Cœur du métier, sans interface
<!-- La chaîne principale, utilisable en ligne de commande, testée de bout en bout avec des services simulés. -->
- [ ] …
- [ ] Commande qui enchaîne tout → premier résultat de bout en bout

## Phase 2 — Interface
- [ ] …

## Phase 3 — Confort et finitions
- [ ] …

## Phase 4 — Mise en service
- [ ] Vérification de la machine cible (ressources, ports, autres applications)
- [ ] Essais réels des services internes depuis le réseau de l'établissement
- [ ] Documentation d'installation
- [ ] Environnement de test, validé par l'utilisateur
- [ ] Mise en production (uniquement après validation de l'utilisateur)

## Phase 5 — Évolutions
- [ ] …

## Idées pour plus tard
- …
