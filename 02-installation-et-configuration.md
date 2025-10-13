# Leçon 2 : Installation et Configuration de Git

Maintenant que nous savons ce qu'est Git, il est temps de l'installer sur votre machine et de le configurer.

## Installation de Git

Git est compatible avec tous les principaux systèmes d'exploitation.

### Windows

Le moyen le plus simple d'installer Git sur Windows est de télécharger et d'installer **Git for Windows** depuis le site officiel : [https://git-scm.com/download/win](https://git-scm.com/download/win).

L'installeur vous guidera. Vous pouvez laisser les options par défaut, elles sont généralement bien adaptées pour commencer.

### macOS

Si vous avez déjà les outils de développement Xcode, Git est probablement déjà installé. Pour vérifier, ouvrez un terminal et tapez :

```bash
git --version
```

Si vous ne l'avez pas, le plus simple est de l'installer avec **Homebrew**, un gestionnaire de paquets pour macOS. Si vous n'avez pas Homebrew, installez-le d'abord. Ensuite, tapez dans le terminal :

```bash
brew install git
```

### Linux (Debian/Ubuntu)

Sur les distributions basées sur Debian comme Ubuntu, vous pouvez l'installer très facilement via le gestionnaire de paquets `apt`. Ouvrez un terminal et tapez :

```bash
sudo apt update
sudo apt install git
```

## Configuration initiale

Une fois Git installé, il y a deux configurations essentielles à faire. Elles sont importantes car elles seront utilisées pour identifier l'auteur de chaque commit que vous ferez.

Ouvrez un terminal (ou Git Bash sur Windows) et tapez les commandes suivantes, en remplaçant les exemples par vos propres informations.

### 1. Configurer votre nom d'utilisateur

Ce nom sera visible dans l'historique de vos projets.

```bash
git config --global user.name "Votre Nom"
```

### 2. Configurer votre adresse e-mail

Cette adresse e-mail sera également attachée à vos commits. Utilisez la même adresse que celle de votre compte GitHub si vous en avez un.

```bash
git config --global user.email "votre.email@example.com"
```

L'option `--global` signifie que cette configuration s'appliquera à tous les projets Git que vous utiliserez sur votre machine. Vous pouvez également configurer ces informations pour un seul projet en omettant l'option `--global` et en lançant la commande depuis le répertoire du projet.

## Vérifier votre configuration

Pour vérifier que les informations ont bien été enregistrées, vous pouvez utiliser la commande suivante :

```bash
git config --list
```

Vous devriez voir, parmi d'autres options, les lignes `user.name` et `user.email` que vous venez de définir.

Et voilà ! Git est installé et prêt à être utilisé. Dans la prochaine leçon, nous allons créer notre premier dépôt et apprendre les commandes de base.
