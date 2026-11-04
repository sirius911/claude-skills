# Questionnaire de démarrage

Ne pose que ce qui manque, par groupes de 3 à 5 questions, dans cet ordre. Une réponse « je ne sais pas »
est normale : propose une option par défaut raisonnable, ou range la question dans `QUESTIONS.md`.

## 1. L'idée
- Que doit faire l'application ? (laisser décrire librement, même de façon décousue ou dictée)
- Qui va l'utiliser, et combien de personnes ?
- Que reçoit-elle en entrée (fichiers, saisies, données d'un autre système) et que produit-elle ?
- À quoi ressemble une utilisation typique, du début à la fin ? (en tirer le « parcours utilisateur »)
- Qu'est-ce qui serait un succès pour une première version ? Qu'est-ce qui peut attendre ?

## 2. L'existant à réutiliser
- Y a-t-il des services ou serveurs existants à utiliser (API interne, modèle d'IA, base de données,
  annuaire) ? Pour chacun : adresse, méthode d'appel, format de réponse, authentification, et si
  possible un exemple d'appel qui fonctionne.
- Des outils ou bibliothèques imposés ou souhaités (liens) ?
- Du code ou des données existants ?

## 3. Le type d'application
Si l'utilisateur hésite, recommande et justifie (installation, mises à jour, accès aux services internes,
puissance nécessaire, confidentialité) :
- application web hébergée sur un serveur / une VM ;
- application de bureau (Windows, macOS…) ;
- outil en ligne de commande ou script ;
- application mobile.

## 4. L'hébergement (si serveur)
- Quelle machine : système, processeurs, mémoire, disque, volumes disponibles ?
- Moteur de conteneurs disponible (Docker, Podman, aucun) et sa version ?
- La machine héberge-t-elle déjà d'autres applications à ne pas perturber ? (ports, ressources, isolation)
- Accès Internet depuis cette machine (pour installer paquets, images, modèles) : direct, via proxy, aucun ?

## 5. Accès et données
- Qui peut accéder ? Libre sur le réseau interne, mot de passe simple, comptes de l'établissement (SSO) ?
- Niveau de sécurité attendu (sans en faire trop pour un petit outil interne).
- Données confidentielles ? Peuvent-elles sortir de l'établissement (services en ligne) ou non ?

## 6. Préférences et façon de travailler
- Langage ou technologie préférés (ou imposés par l'équipe qui maintiendra) ?
- Qui validera les versions avant la mise en production ?
- Travail en console sur un poste, en sessions cloud, ou les deux ? Sessions automatiques souhaitées ?
