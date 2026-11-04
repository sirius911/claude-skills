---
name: nouveau-projet
description: Démarre un nouveau projet logiciel avec la méthode de travail continue (SPEC, PLAN, IDEES, QUESTIONS, JOURNAL, CLAUDE.md) - entretien guidé, vérification du dépôt Git, création des fichiers, validation du plan.
argument-hint: "[adresse du dépôt Git] [description courte]"
disable-model-invocation: true
---

# Nouveau projet : mise en place de la méthode de travail continue

Tu mets en place un projet pour qu'il puisse ensuite avancer **session après session**, y compris en
sessions automatiques, sans perdre le fil. Tout se joue dans des fichiers Markdown versionnés dans Git :
c'est eux, et non la mémoire de la conversation, qui portent le projet.

À la fin, le dépôt contient :

| Fichier | Rôle |
|---|---|
| `SPEC.md` | Ce que fait l'application (le « quoi »), validé par l'utilisateur |
| `PLAN.md` | Les tâches, découpées en phases, avec cases à cocher |
| `IDEES.md` | Boîte à idées de l'utilisateur, intégrée au plan à chaque session |
| `QUESTIONS.md` | Décisions qui reviennent à l'utilisateur ; il répond dans le fichier |
| `JOURNAL.md` | Historique des sessions, la plus récente en haut |
| `CLAUDE.md` | Règles de travail lues automatiquement à chaque session |
| `README.md` | Installation et utilisation, pour un humain |

Les modèles sont dans `modeles/` (à côté de ce fichier). Ce sont des **squelettes** : remplis-les avec
le contenu réel du projet, remplace `{{NOM}}` et `{{DATE}}`, retire les commentaires `<!-- ... -->` et
les sections sans objet. Le modèle de `CLAUDE.md` s'appelle `CLAUDE-modele.md` (pour ne pas être pris
pour des consignes) : il devient `CLAUDE.md` dans le projet.

## Principes
- **Langue** : celle de l'utilisateur (le français par défaut). Pas de jargon : l'utilisateur n'est pas
  forcément développeur ; explique un terme technique la première fois qu'il apparaît.
- **Questions par petits groupes** (3 à 5 à la fois), jamais un formulaire de 20 questions.
  Utilise l'outil de questions à choix quand les options sont nettes (type d'hébergement, connexion…),
  du texte libre sinon.
- **Propose, ne fais pas choisir à l'aveugle** : pour chaque choix technique, donne ta recommandation
  et pourquoi, en une ou deux phrases. L'utilisateur valide ou corrige.
- **Ne bloque pas sur l'inconnu** : ce qui reste sans réponse va dans `QUESTIONS.md`, avec ce que ça bloque.
- **Aucune ligne de code avant la validation du plan.**

Si `$ARGUMENTS` contient déjà une adresse de dépôt ou une description, pars de là et ne redemande pas.

## Étape 1 — Comprendre le projet
Suis `questionnaire.md` (à côté de ce fichier). Commence par laisser l'utilisateur décrire son idée
librement, puis pose seulement les questions dont la réponse manque. Après chaque groupe, reformule en
2-3 lignes ce que tu as compris, pour qu'il puisse corriger tôt.

Si l'utilisateur cite un outil, une bibliothèque ou un dépôt (ex. un lien GitHub), **va le lire** avant de
proposer quoi que ce soit : langues gérées, besoins matériels, licences, façon de l'installer.

## Étape 2 — Le dépôt Git
1. Demande l'adresse du dépôt (s'il n'en a pas : lui expliquer comment en créer un vide sur github.com).
2. Clone-le. S'il **n'est pas vide**, lis ce qui existe : ne jamais écraser un fichier existant sans
   l'avoir lu et sans accord ; fusionne plutôt (ex. un `CLAUDE.md` existant est complété, pas remplacé).
3. **Vérifie tout de suite l'accès en écriture** : fais un premier commit (au minimum `.gitignore`) et pousse.
   Si c'est refusé, explique précisément quoi faire (en général : installer l'application GitHub de Claude
   sur le dépôt, ou reconnecter GitHub) et attends que ce soit réglé avant de continuer.
4. Crée la branche de travail `dev` à partir de `main` et pousse-la.

## Étape 3 — Vérifier l'environnement
Ce qui n'est pas vérifié au début coûte cher plus tard. Fais le tour, et note les résultats :
- **Accès réseau** : pour chaque service externe nécessaire (dépôts de paquets, téléchargement de
  modèles, API), teste qu'il est joignable **depuis l'endroit où tu travailles**. En session cloud,
  certains domaines peuvent être bloqués par la politique réseau de l'environnement : liste ceux à
  autoriser.
- **Services internes** (serveurs de l'établissement, bases de données…) : ils ne sont généralement pas
  joignables depuis une session cloud. Prévois dès le départ un **adaptateur simulé** pour les tests,
  et note quels essais devront être faits en vrai, depuis le réseau interne.
- **Outils** disponibles (langage, ffmpeg, moteur de conteneurs…) sur la machine de travail et sur la
  machine d'hébergement.

## Étape 4 — Créer les fichiers
À partir des modèles de `modeles/` :
- `SPEC.md` : objectif, utilisateurs, parcours utilisateur étape par étape, briques techniques,
  contraintes, hors périmètre. Écrit pour être relu par l'utilisateur, pas par un développeur.
- `PLAN.md` : choix techniques (avec leur justification), puis des phases. Découpage habituel :
  0. **Socle** : structure, configuration, tests automatiques, intégration continue, fichiers de déploiement.
  1. **Cœur du métier** utilisable sans interface (ligne de commande), testé de bout en bout avec des
     services simulés : prouver tôt que l'idée fonctionne.
  2. **Interface** utilisateur.
  3. **Confort et finitions**.
  4. **Mise en service** : vérifications sur la machine cible, environnement de test validé par
     l'utilisateur, puis production (uniquement après son accord).
  5. **Évolutions** déjà évoquées.
  Chaque tâche est petite (une session peut en faire plusieurs) et vérifiable.
- `QUESTIONS.md` : tout ce qui reste ouvert, avec ce que chaque question bloque. Les réponses déjà
  obtenues vont dans « Résolues » (c'est la trace des décisions).
- `IDEES.md` : vide, avec les idées déjà évoquées pendant l'entretien dans « Intégrées ».
- `JOURNAL.md` : première entrée « Démarrage ».
- `CLAUDE.md` : les règles de travail (modèle presque tel quel), plus les règles propres au projet
  (données confidentielles, commandes de test, ce qui ne doit jamais être fait).
- `README.md` : court ; il s'étoffera au fil du projet.
- `.gitignore` adapté au langage, incluant `.env` et les données réelles.

Commit sur `main` (« Démarrage du projet : descriptif, plan et règles de travail »), puis pousse `main`
et `dev`.

## Étape 5 — Validation
Présente à l'utilisateur, en peu de mots :
- le résumé de `SPEC.md` (ce que fera l'application) ;
- les phases de `PLAN.md` et les choix techniques proposés ;
- les questions ouvertes, en commençant par celles qui bloquent le démarrage ;
- ce qui ne pourra être testé qu'en vrai (et où).

Demande-lui de valider ou corriger. Intègre ses corrections dans les fichiers, commit, pousse.

## Étape 6 — La suite
Explique comment le projet vivra désormais :
- Il note ses idées dans `IDEES.md` et répond dans `QUESTIONS.md` (directement sur GitHub ou en local).
- Chaque session (console, cloud ou automatique) commence par relire ces fichiers : il suffit de dire
  « Lis CLAUDE.md et reprends le travail ».
- Toujours récupérer (`git pull`) avant et pousser après ; éviter deux sessions en même temps.

Propose enfin de **programmer des sessions automatiques** (tâches planifiées). Si oui, demande les
horaires et la fréquence (ex. jours ouvrés, quelques sessions courtes entre 8 h et 17 h), et donne à
chaque session une consigne autonome du type : « Lis CLAUDE.md, applique la procédure de début de session,
réalise au plus N tâches du plan, puis applique la procédure de fin de session. » Ne crée la tâche
planifiée qu'après son accord explicite.

Puis, si l'utilisateur le souhaite, commence la phase 0 en suivant `CLAUDE.md`.
