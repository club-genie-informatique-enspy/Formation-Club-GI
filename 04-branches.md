# Leçon 4 : La Puissance des Branches

Jusqu'à présent, nous avons travaillé sur une seule ligne temporelle, la branche `master` (ou `main`). Les branches sont sans doute la fonctionnalité la plus puissante de Git. Elles vous permettent de diverger de la ligne principale de développement pour travailler sur une nouvelle fonctionnalité, un correctif, ou une expérimentation en toute sécurité, sans affecter le projet principal.

## Qu'est-ce qu'une branche ?

Imaginez une branche comme un pointeur mobile vers un commit. Quand vous créez une branche, vous créez simplement un nouveau pointeur. C'est extrêmement léger et rapide.

Le workflow est le suivant :
1.  Vous travaillez sur la branche principale (`master`).
2.  Vous décidez de développer une nouvelle fonctionnalité.
3.  Vous créez une nouvelle branche (ex: `feature/login`).
4.  Vous basculez sur cette nouvelle branche et vous y faites vos modifications et commits.
5.  Pendant ce temps, si un bug critique apparaît sur la version principale, un autre développeur peut créer une branche `hotfix/bug-urgent` depuis `master`, le corriger, et fusionner son correctif dans `master` sans que votre travail sur la fonctionnalité ne soit impacté.
6.  Une fois votre fonctionnalité terminée et testée, vous la "fusionnez" (merge) dans la branche `master`.

```
      C3---C4---C5   <-- feature/login (HEAD)
     /
C1---C2---C6---C7   <-- master
```

## Commandes pour gérer les branches

### `git branch`

Cette commande, utilisée seule, liste toutes les branches de votre dépôt local. L'étoile `*` indique la branche sur laquelle vous vous trouvez actuellement.

```bash
# Lister les branches
git branch

# Créer une nouvelle branche
git branch nom-de-la-branche
```

### `git checkout`

Cette commande permet de se "déplacer" d'une branche à une autre.

```bash
# Se déplacer sur une branche existante
git checkout nom-de-la-branche
```

Vous pouvez combiner la création et le déplacement en une seule commande avec l'option `-b`.

```bash
# Créer la branche ET se déplacer dessus directement
git checkout -b nouvelle-branche
```
C'est la commande que vous utiliserez le plus souvent pour démarrer une nouvelle tâche.

### `git merge`

Une fois que le travail sur votre branche est terminé, vous voudrez l'intégrer à votre branche principale (par exemple, `master`). C'est ce qu'on appelle une fusion (merge).

```bash
# 1. D'abord, revenez sur la branche qui va RECEVOIR les modifications
git checkout master

# 2. Ensuite, lancez la fusion avec la branche que vous voulez intégrer
git merge nom-de-la-branche-a-fusionner
```

Git va alors tenter de combiner les historiques. Si les modifications ne sont pas en conflit, la fusion se fait automatiquement.

      C3---C4---C5      <-- feature/login
     /            \
C1---C2---C6---C7---M   <-- master (HEAD)

Le commit `M` est un "merge commit", il a deux parents et réunit les deux historiques.

### `git branch -d`


Une fois qu'une branche a été fusionnée, elle n'est généralement plus utile. Vous pouvez la supprimer pour garder votre dépôt propre.

```bash
# Supprimer une branche (uniquement si elle a été fusionnée)
git branch -d nom-de-la-branche
```

## Exemple pratique

1.  Vous êtes sur `master`.
2.  Créez et basculez sur une branche pour une nouvelle page "Contact" :
    `git checkout -b feature/page-contact`
3.  Créez le fichier `contact.html` et faites un commit.
    `git add contact.html`
    `git commit -m "feat: ajoute la page contact"`
4.  Votre fonctionnalité est terminée. Revenez sur `master` :
    `git checkout master`
5.  Fusionnez votre travail :
    `git merge feature/page-contact`
6.  Nettoyez en supprimant la branche :
    `git branch -d feature/page-contact`

Les branches sont un outil essentiel pour un travail organisé et collaboratif. Dans la prochaine leçon, nous verrons comment interagir avec un dépôt distant comme GitHub.
