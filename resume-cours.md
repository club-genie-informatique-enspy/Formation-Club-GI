# Semaine 1 : Introduction & Bases du Langage C

## Séance 1 (2h30) : Histoire, compilation, premier programme

---

### 1. Contexte Historique du Langage C

#### 1.1 Genèse du C

Le langage C a été créé entre 1969 et 1973 par **Dennis Ritchie** aux laboratoires Bell (Bell Labs) d'AT&T. Cette création s'inscrit dans un contexte particulier :

**Pourquoi le C a été créé ?**
- Pour développer le système d'exploitation UNIX
- Besoin d'un langage plus portable que l'assembleur
- Alternative aux langages de haut niveau trop lents

**Évolution chronologique :**
- **1969-1970** : Langage B (prédécesseur du C) créé par Ken Thompson
- **1972** : Première version du C par Dennis Ritchie
- **1978** : Publication du livre "The C Programming Language" (K&R C)
- **1989** : Standardisation ANSI C (C89)
- **1999** : Standard C99 (nouvelles fonctionnalités)
- **2011** : Standard C11 (threading, atomics)
- **2018** : Standard C17/C18 (corrections mineures)

#### 1.2 Liens avec UNIX

Le C et UNIX sont indissociables :

- UNIX a été réécrit en C en 1973 (initialement en assembleur)
- Cette réécriture a rendu UNIX portable sur différentes machines
- Le C est devenu le langage de référence pour la programmation système
- Aujourd'hui, Linux, macOS, BSD sont tous écrits majoritairement en C

**Pourquoi cette relation est importante ?**
- Le C donne accès direct aux appels système
- Performance proche de l'assembleur avec syntaxe lisible
- Contrôle total sur la mémoire et le matériel

#### 1.3 Héritage et Influence

Le C a influencé de nombreux langages modernes :

- **C++** : Extension orientée objet du C
- **Java** : Syntaxe inspirée du C
- **Python** : Interpréteur écrit en C (CPython)
- **JavaScript** : Syntaxe influencée par C
- **C#** : Nom et syntaxe inspirés de C
- **Go** : Créé par des pionniers du C chez Google

#### 1.4 Pourquoi le C reste central aujourd'hui ?

Malgré son âge, le C reste incontournable pour :

**Systèmes embarqués :**
- Microcontrôleurs (Arduino, ESP32, STM32)
- Systèmes temps réel
- Firmware de périphériques

**Systèmes d'exploitation :**
- Noyaux (Linux, Windows, macOS)
- Drivers matériels
- Modules système

**Performance critique :**
- Moteurs de jeux (parties critiques)
- Bases de données (PostgreSQL, MySQL)
- Compilateurs et interpréteurs
- Traitement signal/image

**Avantages du C :**
- Performance maximale (proche du matériel)
- Portabilité exceptionnelle
- Contrôle total de la mémoire
- Petit runtime (pas de garbage collector)
- Standard stable et mature

---

### 2. Outils & Environnement de Travail

Pour programmer en C, vous aurez besoin d'un ensemble d'outils. Voici comment les installer et les utiliser.

#### 2.1 Installation de GCC (GNU Compiler Collection)

GCC est le compilateur C le plus utilisé, gratuit et open-source.

**Sur Linux (Ubuntu/Debian) :**
```bash

sudo apt update

sudo apt install build-essential

gcc --version  # Vérifier l'installation

```

**Sur macOS :**
```bash

# Installer Xcode Command Line Tools

xcode-select --install

gcc --version

```

**Sur Windows :**
- Installer MinGW-w64 ou
- Utiliser WSL (Windows Subsystem for Linux) - recommandé

**Vérification :**
```bash

gcc --version

# Devrait afficher : gcc (GCC) x.x.x

```

#### 2.2 Make : Automatiser la compilation

Make est un outil qui automatise le processus de compilation.

**Installation :**
```bash

# Linux

sudo apt install make



# macOS (inclus avec Xcode tools)

make --version



# Windows (avec MinGW)

# Déjà inclus ou installer séparément

```

**Pourquoi utiliser Make ?**
- Évite de retaper les commandes de compilation
- Recompile uniquement les fichiers modifiés
- Gère les projets multi-fichiers
- Standard dans les projets C/C++

#### 2.3 GDB : Le Débogueur

GDB (GNU Debugger) permet de déboguer vos programmes.

**Installation :**
```bash

# Linux

sudo apt install gdb



# macOS

brew install gdb



# Windows (MinGW)

# Inclus avec MinGW

```

**Utilité :**
- Exécuter le programme pas à pas
- Examiner les variables
- Placer des points d'arrêt
- Analyser les crashs (segmentation fault)

#### 2.4 Valgrind : Détection d'erreurs mémoire

Valgrind détecte les fuites mémoire et erreurs d'accès.

**Installation :**
```bash

# Linux

sudo apt install valgrind



# macOS

brew install valgrind

```

**Note :** Valgrind n'est pas disponible nativement sur Windows.

**Pourquoi Valgrind ?**
- Détecte les fuites mémoire (memory leaks)
- Trouve les accès invalides (buffer overflow)
- Identifie l'utilisation de mémoire non initialisée
- Essentiel pour du code robuste

#### 2.5 VS Code : Éditeur de Code

Visual Studio Code est un éditeur moderne, gratuit et puissant.

**Installation :**
1. Télécharger depuis https://code.visualstudio.com/
2. Installer les extensions essentielles :
   - **C/C++** (Microsoft) - IntelliSense, debugging
   - **C/C++ Extension Pack** - Collection d'outils
   - **Code Runner** - Exécution rapide

**Configuration pour C :**

Créer `.vscode/tasks.json` pour compiler :
```json

{

    "version": "2.0.0",

    "tasks": [

        {

            "label": "Compiler C",

            "type": "shell",

            "command": "gcc",

            "args": [

                "-g",

                "${file}",

                "-o",

                "${fileDirname}/${fileBasenameNoExtension}"

            ],
            "group": {

                "kind": "build",

                "isDefault": true

            }

        }

    ]

}

```

**Raccourcis utiles dans VS Code :**
- `Ctrl+Shift+B` : Compiler
- `F5` : Déboguer
- `Ctrl+K Ctrl+C` : Commenter
- `Ctrl+K Ctrl+U` : Décommenter

#### 2.6 Organisation d'un Projet C

Structure recommandée pour vos projets :

```

mon_projet/

├── src/           # Fichiers source (.c)

├── include/       # Fichiers d'en-tête (.h)

├── obj/           # Fichiers objets (.o)

├── bin/           # Exécutables

├── Makefile       # Automatisation compilation

└── README.md      # Documentation

```

**Fichiers C et leurs extensions :**
- `.c` : Fichiers source (code)
- `.h` : Fichiers d'en-tête (headers, déclarations)
- `.o` : Fichiers objets (code compilé non lié)
- Pas d'extension : Exécutable final (Linux/macOS)
- `.exe` : Exécutable Windows

#### 2.7 Introduction aux Makefiles

Un Makefile basique pour un projet simple :

```makefile

# Variables

CC = gcc

CFLAGS = -Wall -Wextra -g

TARGET = mon_programme



# Règle par défaut

all: $(TARGET)



# Compilation

$(TARGET): main.c

	$(CC) $(CFLAGS) main.c -o $(TARGET)



# Nettoyage

clean:

	rm -f $(TARGET)



# Exécution

run: $(TARGET)

	./$(TARGET)

```

**Utilisation :**
```bash

make          # Compile

make run      # Compile et exécute

make clean    # Supprime l'exécutable

```

**Explication des options GCC courantes :**
- `-Wall` : Active tous les avertissements
- `-Wextra` : Avertissements supplémentaires
- `-g` : Ajoute informations de débogage
- `-O2` : Optimisation niveau 2
- `-o` : Spécifie le nom de sortie

---

### 3. Premier Programme et Analyse Ligne par Ligne

#### 3.1 Le Programme "Hello, World!"

Voici votre premier programme en C :

```c

#include <stdio.h>



int main() {

    printf("Hello, C!\n");

    return 0;

}

```

#### 3.2 Analyse Détaillée Ligne par Ligne

**Ligne 1 : `#include <stdio.h>`**

```c

#include <stdio.h>

```

- `#include` : Directive du préprocesseur (pas du C lui-même)
- Demande d'inclure le contenu d'un fichier
- `<stdio.h>` : Standard Input/Output (entrées/sorties standard)
- Les `< >` indiquent un fichier système
- Ce fichier contient la déclaration de `printf`, `scanf`, etc.

**Sans cette ligne, le programme ne compilerait pas car `printf` serait inconnu.**

**Ligne 3 : `int main() {`**

```c

int main() {

```

- `int` : Type de retour (integer = nombre entier)
- `main` : Nom de la fonction principale
- **Particularité :** `main` est le point d'entrée du programme
- `()` : Liste de paramètres (vide ici)
- `{` : Début du bloc de la fonction

**Tout programme C doit avoir une fonction `main`.**

**Ligne 4 : `printf("Hello, C!\n");`**

```c

printf("Hello, C!\n");

```

- `printf` : Fonction d'affichage formaté (print formatted)
- `"Hello, C!\n"` : Chaîne de caractères (string)
- `\n` : Caractère spécial pour nouvelle ligne (newline)
- `;` : Termine l'instruction (obligatoire)

**Caractères d'échappement courants :**
- `\n` : Nouvelle ligne
- `\t` : Tabulation
- `\\` : Backslash littéral
- `\"` : Guillemet dans une chaîne
- `\r` : Retour chariot

**Ligne 5 : `return 0;`**

```c

return 0;

```

- `return` : Retourne une valeur à celui qui a appelé
- `0` : Convention indiquant succès
- Valeur non-nulle = erreur

**Convention :**
- `0` = Programme terminé avec succès
- `1` (ou autre) = Erreur

**Ligne 6 : `}`**

```c

}

```

- Ferme le bloc de la fonction `main`

#### 3.3 Compilation Étape par Étape

La compilation d'un programme C se fait en plusieurs phases :

**Phase 1 : Préprocesseur**
```bash

gcc -E main.c -o main.i

```

- Traite les directives `#include`, `#define`
- Remplace les macros
- Supprime les commentaires
- Produit un fichier `.i` (code C pur)

**Phase 2 : Compilation**
```bash

gcc -S main.i -o main.s

```

- Traduit le C en assembleur
- Produit un fichier `.s` (code assembleur)
- Optimisations appliquées ici

**Phase 3 : Assemblage**
```bash

gcc -c main.s -o main.o

```

- Traduit l'assembleur en code machine
- Produit un fichier `.o` (fichier objet)
- Code binaire mais pas encore exécutable

**Phase 4 : Édition de Liens (Linking)**
```bash

gcc main.o -o main

```

- Lie les fichiers objets entre eux
- Ajoute les bibliothèques nécessaires
- Produit l'exécutable final

**Tout en une commande :**
```bash

gcc main.c -o main

```

**Exécution :**
```bash

./main          # Linux/macOS

main.exe        # Windows

```

#### 3.4 Erreurs Courantes et Solutions

**Erreur 1 : Point-virgule manquant**

```c

#include <stdio.h>



int main() {

    printf("Hello")  // ERREUR : manque ;

    return 0;

}

```

**Message :**
```

error: expected ';' before 'return'

```

**Solution :** Ajouter `;` après chaque instruction.

**Erreur 2 : Oubli de #include**

```c

int main() {

    printf("Hello\n");  // ERREUR : printf non déclaré

    return 0;

}

```

**Message :**
```

warning: implicit declaration of function 'printf'

```

**Solution :** Ajouter `#include <stdio.h>`.

**Erreur 3 : Type de retour incorrect**

```c

#include <stdio.h>



void main() {  // Mauvaise pratique

    printf("Hello\n");

}

```

**Problème :** `main` doit retourner `int`.

**Bonne pratique :**
```c

int main() {

    printf("Hello\n");

    return 0;

}

```

---

### 4. Exercices Corrigés

#### Exercice 1 : Afficher votre nom, âge et taille

**Énoncé :** Écrivez un programme qui affiche votre nom, votre âge et votre taille.

**Solution :**

```c

#include <stdio.h>



int main() {

    // Déclaration et initialisation des variables

    char nom[] = "Jean Dupont";

    int age = 25;

    float taille = 1.75;

    

    // Affichage avec printf

    printf("Nom : %s\n", nom);

    printf("Age : %d ans\n", age);
    printf("Taille : %.2f m\n", taille);

    

    return 0;
}

```

**Explication détaillée :**

1. **`char nom[] = "Jean Dupont";`**
   - `char` : Type caractère
   - `[]` : Tableau (pour stocker plusieurs caractères)
   - La chaîne est automatiquement terminée par `\0`

2. **`int age = 25;`**
   - `int` : Nombre entier
   - Stocke des valeurs de -2147483648 à 2147483647 (sur 32 bits)

3. **`float taille = 1.75;`**
   - `float` : Nombre à virgule flottante
   - Précision d'environ 6-7 chiffres

4. **Spécificateurs de format dans printf :**
   - `%s` : String (chaîne de caractères)
   - `%d` : Decimal (entier)
   - `%.2f` : Float avec 2 décimales

**Compilation et exécution :**
```bash

gcc exercice1.c -o exercice1
./exercice1

```

**Sortie attendue :**
```

Nom : Jean Dupont

Age : 25 ans

Taille : 1.75 m

```

---

#### Exercice 2 : Rectangle d'étoiles

**Énoncé :** Écrivez un programme qui affiche un rectangle d'étoiles de 5 lignes et 8 colonnes.

**Solution :**

```c

#include <stdio.h>



int main() {

    // Méthode 1 : Affichage direct

    printf("********\n");

    printf("********\n");

    printf("********\n");

    printf("********\n");

    printf("********\n");

    

    return 0;

}

```

**Solution améliorée avec boucles (aperçu):**

```c

#include <stdio.h>



int main() {

    int lignes = 5;

    int colonnes = 8;

    

    // Boucle pour les lignes

    for (int i = 0; i < lignes; i++) {

        // Boucle pour les colonnes
        for (int j = 0; j < colonnes; j++) {

            printf("*");

        }

        printf("\n");  // Nouvelle ligne après chaque rangée

    }

    

    return 0;

}

```

**Note :** Les boucles seront vues en détail à la séance 3.

**Sortie attendue :**
```

********

********

********

********

********

```

---

