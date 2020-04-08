# Git init !

![project logo](https://raw.githubusercontent.com/prahladyeri/enforce-git-message/master/logo.png)

Simple repo d'exemple pour comprendre et appliquer le `rebase` avancé.

Ce guide couvre les commands avancées `fixup`, `squash`, `reword` ou `edit` (pour les plus courageux), et même le changement d'ordre.

## Démarrer

Après l'avoir cloner, vous alleer obtenir un historique qui ressemble à ceci:

```
5121c59 (HEAD -> master) feat(fichier6): J'ai oublié de release ça AVANT la feature 'fichier4'
e97ebd6 feat(fichier5): Noukjqsdj fichier 5
5ab2953 feat(fichier4): wip
d76b9c9 feat(fichier4): wip
685250d feat(fichier4): fix typo
135a5d3 feat(fichier4): Feature numéro 4 yeah!
257b70d feat(fichier1): Fix fichier1
be54579 feat(fichier2): fix typo
a3ba77b feat(fichier2): Nouvelle feature!
20b099b feat(fichier1): Initial commit
```

On peut voir ici, 6 features (nom choisi arbitrairement). Néanmoins le commiter s'est un peu emmêlé les pinceaux…
Le but du jeu, si vous le voulez bien, est de remettre les choses dans l'ordre, ou du moins dans un ordre cohérent, en atteignant un historique comme celui-ci:

```
e97ebd6 (HEAD -> master) feat(fichier5): Nouveau fichier 5
135a5d3 feat(fichier4): Feature numéro 4 yeah!
5121c59 feat(fichier6): J'ai oublié de release ça AVANT la feature 'fichier4'
a3ba77b feat(fichier2): Nouvelle feature!
20b099b feat(fichier1): Initial commit
```

> Il faut ici renommer le commit…

Avec pour fichier dans le répertoire courant:

```
-rw-r--r--  1 quentin  staff  2061 Apr  8 18:51 README.md
-rw-r--r--  1 quentin  staff    45 Apr  8 18:37 file1
-rw-r--r--  1 quentin  staff    85 Apr  8 18:37 file2
-rw-r--r--  1 quentin  staff    44 Apr  8 18:37 file4
-rw-r--r--  1 quentin  staff    44 Apr  8 18:37 file5
-rw-r--r--  1 quentin  staff    44 Apr  8 18:37 file6
```

> Notez la disparition du fichier 3

## Pourquoi je comprend plus rien à l'historique obtenu ?

En effet, pour être sur un remote `origin` qui pointe sur `SkYNewZ/git-init`. Etant donné que vous avez intéragi sur votre repository Git local, les commits distants sont toujours visibles.

Mais alors que faire ?

## Aller plus loin

## L'option edit

L'option `edit` du `rebase` vous permet de modifier le contenu d'un commit: en retirer des fichiers, en ajouter ou les modifier.

Essaie de créer un fichier, puis de le placer **dans** le commit `Nouvelle feature!`.

## Se forcer à faire de jolis messages de commits

Il exite dans Git des hooks. Ce sont des scripts (vides par défaut) qui sont reliés à des évènements de Git. Par exemple:

- Avant de valider
- Après avoir validé
- Avant de pousser
- etc…

Les Git hooks sont faits pour vous faciliter gestes répétitifs: linter du code avant de commit, éxécution des tests unitaires avant de commit, s'imposer une nomenclature pour les messages.
Bien que ce soient de simples scripts shell (ou Python, ou binaire, tant que c'est éxécutable) ils se doivent de rester simples.

Pour celles et ceux qui seraient intéréssés par le fait s'imposer une nomenclature de message de commit, il existe ceci, un exemple de Git hook, fait en Python qui renvoie un exit code 1 si le message ne respecte pas https://www.conventionalcommits.org/.

> https://github.com/prahladyeri/enforce-git-message

Cela permet de générer dee jolis changelogs, automatiquement, rien qu'en lisant vos messages !

> https://github.com/git-chglog/git-chglog

### Le mot de la fin

Merci. Ne faites pas de rebase sur une branche distante protégée. Merci. 😛
Faites votre tambouille sur votre branche de développement, c'est la votre. Faites des `WIP1`, `WIP2`, `WIP3`… a tout va, c'est votre branche et le rebase est fait pour ça: **s'assurer que les commits poussés sont propres en terme de contenu et de message, qu'ils aient une cohérence entre eux**. Considérer la `master` comme un point de non retour.
