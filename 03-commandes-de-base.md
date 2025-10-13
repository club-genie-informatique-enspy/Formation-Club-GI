# Leçon 3 : Commandes de Base de Git

Dans cette leçon, nous allons aborder le cœur du workflow de Git. Ce sont les commandes que vous utiliserez 90% du temps.

## Le workflow en 3 étapes

Git fonctionne avec trois "zones" principales :

1.  **Le Répertoire de Travail (Working Directory)** : C'est votre dossier de projet, là où vous modifiez, créez ou supprimez des fichiers.
2.  **La Zone de Préparation (Staging Area)** : C'est une zone intermédiaire. Vous y ajoutez les modifications que vous souhaitez inclure dans le prochain "instantané" (commit). Cela vous permet de choisir précisément ce qui sera enregistré.
3.  **Le Dépôt (.git)** : C'est là que Git stocke de manière permanente les instantanés de votre projet sous forme de commits.

Le processus est le suivant : Vous modifiez vos fichiers (Working Directory), vous sélectionnez les changements à enregistrer (Staging Area), puis vous les enregistrez définitivement (Dépôt).

```
+----------------------+        +--------------------+        +----------------+
|                      |        |                    |        |                |
|  Répertoire de       | git add|   Staging Area     | git    | Dépôt (.git)   |
|  Travail             |------->|   (Index)          | commit | (Repository)   |
| (Working Directory)  |        |                    |------->|                |
|                      |<-------|                    |        |                |
|                      | git    |                    |        |                |
|                      | checkout                    |        |                |
+----------------------+        +--------------------+        +----------------+
```

## Les commandes essentielles

### `git init`

Nous l'avons vu, mais c'est la commande qui transforme un dossier normal en dépôt Git. Elle crée le sous-dossier caché `.git` qui contient toute la logique du dépôt.

### `git status`

C'est votre meilleur ami. Cette commande vous indique l'état de votre dépôt : quels fichiers sont modifiés, lesquels sont dans la Staging Area, etc. Lancez-la souvent !

```bash
# Affiche l'état actuel du dépôt
git status
```

### `git add`

Cette commande permet d'ajouter des modifications du répertoire de travail à la zone de préparation (Staging Area).

```bash
# Pour ajouter un fichier spécifique
git add nom-du-fichier.txt

# Pour ajouter tous les fichiers modifiés et nouveaux du dossier courant
git add .
```

### `git commit`

C'est l'action d'enregistrer l'instantané de votre Staging Area dans votre dépôt. Chaque commit a un identifiant unique et un message qui décrit les changements.

Le message de commit est **crucial**. Il doit être clair et concis.

```bash
# Ouvre un éditeur de texte pour écrire un message de commit
git commit

# Permet de passer le message directement (pratique pour les petits changements)
git commit -m "Message de commit explicite"
```

### `git log`

Cette commande vous permet de voir l'historique des commits de votre projet. Vous y verrez l'auteur, la date et le message de chaque commit.

```bash
# Affiche l'historique complet
git log

# Affiche un historique simplifié sur une seule ligne par commit
git log --oneline
```

## Exemple de workflow complet

Imaginons un nouveau projet.

1.  On se place dans le dossier du projet.
2.  On initialise le dépôt :
    `git init`
3.  On crée un fichier `index.html`.
4.  On vérifie l'état :
    `git status` (Git nous dira que `index.html` est "untracked" - non suivi).
5.  On l'ajoute à la Staging Area :
    `git add index.html`
6.  On vérifie à nouveau l'état :
    `git status` (Git nous dira que `index.html` est prêt à être commité).
7.  On enregistre notre premier commit :
    `git commit -m "feat: ajout du fichier de base index.html"`
8.  On consulte l'historique :
    `git log`

Vous venez de réaliser le cycle de base de Git ! Dans la prochaine leçon, nous explorerons la fonctionnalité la plus puissante de Git : les branches.
