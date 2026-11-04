# Mes skills Claude Code

Chaque dossier contient un skill (un fichier `SKILL.md` et ses annexes).

| Skill | Commande | Rôle |
|---|---|---|
| [nouveau-projet](nouveau-projet/SKILL.md) | `/nouveau-projet` | Démarrer un projet avec la méthode de travail continue : entretien guidé, vérification du dépôt Git, création de SPEC / PLAN / IDEES / QUESTIONS / JOURNAL / CLAUDE.md, validation du plan |

Les skills ne se déclenchent que si on tape leur commande : ils ne chargent rien et ne coûtent rien le reste du temps.

## Installation sur un ordinateur

Les skills personnels de Claude Code se trouvent dans `~/.claude/skills/`.

**Si ce dossier n'existe pas encore** (cas le plus courant) :

```bash
git clone https://github.com/sirius911/claude-skills.git ~/.claude/skills
```

Sous Windows (PowerShell) :

```powershell
git clone https://github.com/sirius911/claude-skills.git "$env:USERPROFILE\.claude\skills"
```

**S'il existe déjà**, clonez ailleurs puis copiez le dossier du skill :

```bash
git clone https://github.com/sirius911/claude-skills.git ~/claude-skills
cp -r ~/claude-skills/nouveau-projet ~/.claude/skills/
```

Relancez Claude Code : la commande `/nouveau-projet` est disponible dans tous les dossiers.

## Mise à jour

```bash
git -C ~/.claude/skills pull
```

## Utilisation

Dans un dossier vide (ou n'importe où), lancez `claude` puis :

```
/nouveau-projet
```

On peut aussi donner directement le dépôt et une idée :

```
/nouveau-projet https://github.com/moi/mon-projet.git une application qui …
```

## Dans les sessions cloud (claude.ai/code)

Les skills de `~/.claude/skills/` sont sur votre ordinateur : une session cloud ne les voit pas.
Pour une session cloud, ajoutez ce dépôt à la session et demandez :
« Lis `nouveau-projet/SKILL.md` dans claude-skills et applique-le pour mon nouveau projet. »
