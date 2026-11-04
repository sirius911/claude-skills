# Règles de travail pour Claude

## Langue
- Tout en français : documents, messages de commit, textes de l'interface.
- Le code (noms de variables, fonctions) peut rester en anglais.

## Début de chaque session
1. `git pull` sur la branche de travail.
2. Lire SPEC.md, PLAN.md, QUESTIONS.md et les 2-3 dernières entrées de JOURNAL.md.
3. Lire IDEES.md : intégrer chaque nouvelle idée dans PLAN.md (à la bonne phase), puis la déplacer dans « Intégrées ».
   Si une idée est ambiguë ou contredit SPEC.md, poser la question dans QUESTIONS.md au lieu de deviner.
4. Lire les réponses dans QUESTIONS.md, les reporter (SPEC/PLAN), et déplacer les questions dans « Résolues ».

## Pendant la session
- Prendre la prochaine tâche `[ ]` non bloquée de PLAN.md, dans l'ordre des phases.
- Petites étapes : une tâche = un commit, avec des tests qui passent.
- Les tests ne dépendent jamais des vrais services internes : utiliser les versions simulées.
- Une décision qui revient à l'utilisateur → l'écrire dans QUESTIONS.md et passer à une autre tâche.
- Ne pas ajouter de fonctionnalité absente de SPEC.md / PLAN.md.
- Ce qui n'a pas pu être vérifié en vrai est marqué `[~]` avec la raison, jamais `[x]`.

## Fin de chaque session
- Mettre à jour les cases de PLAN.md.
- Ajouter une entrée en haut de JOURNAL.md : ce qui a été fait, ce qui n'a pas été vérifié, ce qui bloque, la suite.
- Commit et push sur la branche de travail.

## Sessions automatiques
- Réaliser au plus le nombre de tâches indiqué dans la consigne de la session.
- S'arrêter proprement (procédure de fin de session) si tout est bloqué par des questions.
- Ne jamais déployer, supprimer de données ou modifier `main` lors d'une session automatique.

## Branches et déploiement
- Travail sur la branche `dev` ; `main` = version validée par l'utilisateur.
- Aucun déploiement en production sans validation explicite de l'utilisateur.

## Données et secrets
- Ne jamais committer de secrets (`.env`, mots de passe, clés) ni de données réelles.
<!-- Règles propres au projet : confidentialité, services autorisés, commandes de test… -->
