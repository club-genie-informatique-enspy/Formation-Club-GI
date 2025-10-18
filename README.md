# Formations Club GI

Bienvenue dans le dépôt des formations du Club GI. Ce dépôt contient plusieurs formations, chacune accessible dans une branche Git dédiée.

## Tutoriel : Comment accéder aux cours

Suivez ces étapes pour commencer une formation.

### 1. Cloner le dépôt

Tout d'abord, vous devez cloner ce dépôt sur votre machine locale. Ouvrez un terminal et exécutez la commande suivante :

```bash
git clone https://github.com/club-genie-informatique-enspy/Formation-Club-GI.git
```

Une fois le clonage terminé, déplacez-vous dans le répertoire du projet :

```bash
cd Formation-Club-GI
```

### 2. Choisir et commencer un cours

Par défaut, vous serez sur la branche `main`. Cette branche contient cette documentation. Pour accéder à un cours, vous devez "checker" la branche correspondante.

Par exemple, pour commencer la formation sur **Python**, utilisez la commande :

```bash
git checkout formation-python
```

Les fichiers du cours (documents, exercices, etc.) seront alors disponibles dans votre répertoire.

### 3. Passer d'un cours à un autre

Vous pouvez changer de formation à tout moment. Si vous souhaitez passer à la formation sur le **Développement Web**, par exemple, assurez-vous que vos modifications actuelles sont "commitées" ou "stashées", puis exécutez :

```bash
git checkout formation-web
```

Pour revenir à ce `README` principal, retournez simplement sur la branche `main` :

```bash
git checkout main
```

## Liste des formations disponibles

Voici la liste des formations actuellement disponibles. Utilisez la commande `git checkout [nom-de-la-branche]` pour y accéder.

*   **Git et GitHub :** `formation-git-github`
*   **Réseau :** `formation-en-reseau`
*   **Flutter :** `formation-flutter`
*   **Java Spring Boot :** `formation-java-spring-boot`
*   **Programmation Système en C :** `formation-prog-sys-C`
*   **Python :** `formation-python`
*   **Développement Web :** `formation-web`

---

# Club GI Training

Welcome to the Club GI training repository. This repository contains several courses, each accessible in a dedicated Git branch.

## Tutorial: How to Access the Courses

Follow these steps to start a course.

### 1. Clone the Repository

First, you need to clone this repository to your local machine. Open a terminal and run the following command:

```bash
git clone https://github.com/club-genie-informatique-enspy/Formation-Club-GI.git
```

Once cloning is complete, navigate into the project directory:

```bash
cd Formation-Club-GI
```

### 2. Choose and Start a Course

By default, you will be on the `main` branch, which contains this documentation. To access a course, you need to "check out" the corresponding branch.

For example, to start the **Python** course, use the command:

```bash
git checkout formation-python
```

The course files (documents, exercises, etc.) will then be available in your directory.

### 3. Switch Between Courses

You can switch courses at any time. If you want to switch to the **Web Development** course, for example, make sure your current changes are committed or stashed, then run:

```bash
git checkout formation-web
```

To return to this main `README`, simply go back to the `main` branch:

```bash
git checkout main
```

## List of Available Courses

Here is the list of currently available courses. Use the `git checkout [branch-name]` command to access them.

*   **Git and GitHub:** `formation-git-github`
*   **Networking:** `formation-en-reseau`
*   **Flutter:** `formation-flutter`
*   **Java Spring Boot:** `formation-java-spring-boot`
*   **System Programming in C:** `formation-prog-sys-C`
*   **Python:** `formation-python`
*   **Web Development:** `formation-web`