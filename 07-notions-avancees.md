# Leçon 7 : Notions Avancées et Bonnes Pratiques

Maintenant que vous maîtrisez le workflow de base, explorons des commandes et des concepts plus avancés qui vous rendront encore plus productif et professionnel.

## `git rebase` : Réécrire l'histoire proprement

Quand vous fusionnez une branche avec `git merge`, cela crée un "commit de fusion". C'est bien, mais parfois, cela peut rendre l'historique difficile à lire, avec plein de branches qui se croisent.

`git rebase` est une alternative. Au lieu de créer un commit de fusion, il prend les commits de votre branche de fonctionnalité et les rejoue *au-dessus* des derniers changements de la branche `master`. Le résultat est un historique **linéaire** et beaucoup plus propre.

```bash
# Depuis votre branche de fonctionnalité
git rebase master
```

```
AVANT REBASE (identique à un merge) :

      C3---C4---C5   <-- feature
     /
C1---C2---C6---C7   <-- master

APRÈS REBASE :

                     C3'--C4'--C5'  <-- feature
                    /
C1---C2---C6---C7   <-- master
```
Les commits de la branche `feature` ont été re-créés (C3', C4', C5') et placés à la suite de `master`.

**Attention** : N'utilisez `git rebase` que sur des branches que vous n'avez pas encore partagées avec d'autres. Réécrire l'historique d'une branche collaborative peut causer des problèmes complexes.

## `git stash` : Mettre son travail de côté

Imaginez : vous êtes au milieu d'une fonctionnalité, et on vous demande de corriger un bug urgent. Vos modifications ne sont pas prêtes à être commitées. Que faire ?

`git stash` met vos modifications non commitées de côté dans une "réserve" temporaire et nettoie votre répertoire de travail.

```bash
# Mettre les changements en réserve
git stash

# (Maintenant, vous pouvez changer de branche et corriger le bug urgent)

# Une fois terminé, revenez sur votre branche et récupérez votre travail
git stash pop
```

## `git tag` : Marquer les versions

Quand votre projet atteint une version stable (ex: 1.0, 2.5), vous pouvez la marquer avec un "tag". C'est un pointeur permanent vers un commit spécifique, ce qui facilite la consultation des versions publiées.

```bash
# Créer un tag "léger"
git tag v1.0.0

# Pousser les tags vers le dépôt distant (ils ne partent pas par défaut)
git push origin --tags
```

## Le fichier `.gitignore`

Votre projet contient souvent des fichiers qui ne devraient jamais être suivis par Git : dépendances (`node_modules`), fichiers de configuration de votre éditeur (`.vscode`), logs, etc.

Créez un fichier nommé `.gitignore` à la racine de votre projet et listez-y les fichiers ou dossiers à ignorer. Chaque ligne correspond à un motif.

**Exemple de `.gitignore`** :
```
# Dépendances
node_modules/

# Fichiers de log
*.log

# Fichiers système macOS
.DS_Store
```

## Le fichier `.gitattributes`

Moins connu que `.gitignore`, le fichier `.gitattributes` permet de déclarer des attributs spécifiques pour des chemins (fichiers ou dossiers). C'est un outil puissant pour dicter à Git comment il doit traiter certains fichiers.

Créez un fichier `.gitattributes` à la racine de votre projet.

### Cas d'usage 1 : Gérer les fins de ligne (EOL)

Le problème classique : Windows utilise `CRLF` pour les fins de ligne, tandis que Linux et macOS utilisent `LF`. Cela peut créer des "différences" inutiles dans les fichiers. `.gitattributes` résout ce problème.

```
# Forcer Git à toujours utiliser les fins de ligne LF (Linux/Mac) dans le dépôt,
# mais à les convertir en fins de ligne natives du système de l'utilisateur lors du checkout.
* text=auto
```

### Cas d'usage 2 : Git LFS (Large File Storage)

Git n'est pas fait pour versionner de gros fichiers binaires (images HD, vidéos, fichiers audio). Git LFS est une extension qui résout ce problème en stockant des pointeurs dans le dépôt Git, tandis que les gros fichiers eux-mêmes sont stockés sur un serveur dédié.

`.gitattributes` est utilisé pour dire à Git LFS quels fichiers il doit prendre en charge.

```
# Indiquer à Git LFS de gérer tous les fichiers .psd (Photoshop)
*.psd filter=lfs diff=lfs merge=lfs -text
```

## GitHub Actions : Automatiser son workflow

GitHub Actions est un outil de CI/CD (Intégration Continue / Déploiement Continu) intégré à GitHub. Il vous permet d'automatiser des actions en réponse à des événements sur votre dépôt (comme un `push` ou une `Pull Request`).

Créez un dossier `.github/workflows` dans votre projet, et à l'intérieur, un fichier YAML (ex: `main.yml`).

**Exemple simple** : Lancer des tests à chaque push sur `master`.
```yaml
name: CI
on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run tests
      run: npm test # ou la commande de test de votre projet
```

## GitHub Pages : Héberger son site statique

GitHub Pages est un service gratuit qui prend les fichiers HTML, CSS et JavaScript de votre dépôt et les publie en tant que site web.

1.  Allez dans les **Settings** de votre dépôt GitHub.
2.  Dans la section **Pages**, choisissez la branche que vous voulez publier (souvent `master` ou une branche `gh-pages`).
3.  GitHub vous donnera l'URL de votre site (ex: `https://VOTRE_NOM.github.io/VOTRE_DEPOT/`).

C'est un excellent moyen de mettre en ligne un portfolio, une documentation ou la page de présentation d'un projet.
