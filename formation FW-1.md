> # Cours : HTML, CSS et JavaScript 


---
## 1. Introduction
Ce cours a pour objectif de donner une compréhension solide des bases du **développement web frontend** avec **HTML, CSS et JavaScript**.  
Il aborde les concepts fondamentaux puis des techniques plus avancées pour structurer, styliser et rendre une page web interactive.

**Objectifs pédagogiques** :
- Comprendre la structure d'une page web (HTML).
- Savoir styliser une page (CSS) et appréhender la mise en page moderne (Flexbox, Grid).
- Maîtriser les bases de JavaScript (ES6+) pour la logique applicative.
- Être capable de créer un petit projet de catalogue de produits combinant ces notions.

---

## 2. Avant de commencer — Outils et structure d'un projet
Cette section explique ce que doit savoir un débutant avant d'écrire son premier fichier.

### 2.1 Outils recommandés
- **Éditeur de code** : Visual Studio Code (recommandé), Sublime Text, Atom.
- **Navigateurs** : Chrome, Firefox, Edge ou Safari (pour tester vos pages).
- **Terminal** : pour lancer éventuellement un serveur local.
- **Extensions utiles VS Code** : Live Server, Prettier, HTML/CSS/JS snippets.

### 2.2 Structure minimale d'un projet
```
mon-projet/
  ├─ index.html
  ├─ css/
  │   └─ style.css
  ├─ js/
  │   └─ script.js
  └─ assets/
     └─images/
```
- **index.html** : page d'accueil principale.
- **css/style.css** : feuilles de style externes.
- **js/script.js** : code JavaScript (logique, fonctions, algorithmes).

### 2.3 Comment ouvrir votre page
- Méthode simple : double-cliquer sur `index.html` ouvrira la page dans votre navigateur.
- Méthode recommandée : utiliser un mini-serveur (évite certains problèmes de chemins) :
  - Avec l'extension *Live Server* de VS Code, cliquer sur "Go Live" ou taper live-server dans le terminal u niveau du dossier de travail.

---


## 3. Rappel : HTML / CSS / JS

### 3.1. Qu’est-ce que HTML ?
- **HTML (HyperText Markup Language)** est le langage de balisage utilisé pour structurer le contenu d’une page web.
- Les éléments HTML sont représentés par des **balises** : `<h1>`, `<p>`, `<img>`, etc.

Exemple :
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Ma première page</title>
</head>
<body>
  <h1>Bonjour le monde</h1>
  <p>Ceci est mon premier paragraphe.</p>
</body>
</html>
```
- *NOTES HTML*: Le DOCTYPE (Document Type Declaration) est la toute première ligne d'un document HTML. C'est une instruction qui indique au navigateur quelle version de HTML vous utilisez.

      À quoi sert-il ?
          1. Activation du Mode Standard :

              Sans DOCTYPE → Mode Quirks (compatibilité ancienne)

              Avec DOCTYPE → Mode Standard (normes modernes)

#### 3.1.1. Concepts de base à connaître en HTML
- **Balises de base** :
  - `<html>` : Racine du document.
  - `<head>` : Contient les métadonnées (titre, liens CSS, etc.).
  - `<body>` : Contient le contenu visible de la page.
  - `<h1>` à `<h6>` : Titres de niveaux 1 à 6.
  - `<p>` : Paragraphe de texte.
  - `<a>` : Lien hypertexte (attribut `href` pour l'URL).
  - `<img>` : Image (attributs `src` pour le chemin et `alt` pour le texte alternatif).
  - `<ul>` et `<ol>` : Listes non ordonnées et ordonnées, avec `<li>` pour les éléments.
  - `<div>` : Conteneur générique pour grouper des éléments.
  - `<span>` : Conteneur generique pour styliser du texte.
- **Attributs** : Ajoutent des informations aux balises (ex. : `class`, `id`, `style`).
- **Structure générale** : Tout document HTML commence par `<!DOCTYPE html>`, suivi de `<html>`, `<head>` et `<body>`.
- **Commentaires** : `<!-- Commentaire -->` pour ajouter des notes non visibles.

#### 3.1.2. Attributs importants
- `id` : identifiant unique (utilisé pour repérer un élément — n'implique pas de manipulations DOM ici).
- `class` : classe(s) partageables entre éléments.
- `alt` : texte alternatif pour les images (accessibilité).
- `title` : info-bulle au survol.

####3.1.3 Les Formulaires
Un formulaire HTML est une section d'un document qui contient des contrôles interactifs permettant à l'utilisateur de saisir et soumettre des données à un serveur web.

### 3.2. Qu’est-ce que CSS ?
- **CSS (Cascading Style Sheets)** est le langage de style qui permet de contrôler l’apparence des éléments HTML.
- Exemple :
```css
/* Sélectionne l'élément body et applique un style */
body {
  background-color: #f0f0f0;  /* Couleur de fond gris clair */
  font-family: Arial, sans-serif;  /* Police de caractères */
}

/* Sélectionne tous les éléments h1 */
h1 {
  color: darkblue;  /* Couleur du texte bleu foncé */
  text-align: center;  /* Alignement du texte au centre */
}
```
#### 3.2.1. Trois façons d’ajouter du CSS
1. **Externe** : `<link rel="stylesheet" href="css/style.css">` — recommandé.
2. **Interne** : `<style>` dans le `<head>`.
3. **Inline** : attribut `style="..."` — à éviter.

#### 3.2.2. Le modèle de boîte (Box Model) — expliqué en détail
Chaque élément HTML est une boîte composée de :
- **Content** (le contenu)
- **Padding** (espace intérieur entre le contenu et la bordure)
- **Border** (la bordure)
- **Margin** (espace extérieur)

Exemple :
```css
.box {
  width: 200px;       /* largeur du contenu */
  padding: 10px;      /* espace intérieur */
  border: 2px solid #333; /* bordure */
  margin: 20px;       /* espace extérieur */
}
```

#### 3.2.3. Cascade, spécificité et ordre des styles
- **Cascade** : CSS signifie "feuilles de style en cascade" — plusieurs règles peuvent s'appliquer. Le navigateur choisit celle avec la plus grande spécificité ou la dernière déclarée si spécificités égales.
- **Spécificité (règles de priorité)** :
  - Sélecteur d'ID (`#id`) a une forte spécificité.
  - Sélecteur de classe (`.classe`) a une spécificité moyenne.
  - Sélecteur d'élément (`div`, `p`) a une spécificité faible.
  - `!important` force une règle (à éviter sauf cas particulier).

**Exemple** :
```css
p { color: black; }         /* spécificité basse */
.ma-classe { color: green; }/* plus élevé */
#monId { color: red; }      /* encore plus élevé */
```

#### 3.2.4. Unités 
- `px` → pixels (fixe)
- `%` → pourcentage par rapport au parent
- `em` / `rem` → taille relative (em relatif à l'élément, rem relatif à la racine)
- `vh` / `vw` → 1% de la hauteur/largeur du viewport

#### 3.2.5. Sélecteurs utiles
- `.` classe, `#` id, `element` balise, `element > child` (enfant direct), `element:hover` (pseudo-état), `a[href]` (sélecteur d'attribut), etc.

---
    - **Commentaires** : `/* Commentaire */`.

### 3.3. Qu’est-ce que JavaScript ?
- **JavaScript (JS)** est le langage de programmation qui permet de rendre une page web interactive.
- Exemple :
```javascript
document.querySelector("h1").addEventListener("click", () => {
  alert("Vous avez cliqué sur le titre !");
});
```

#### 3.3.1. Concepts de base à connaître en JavaScript
- **Variables** : Déclarées avec `let` (réassignable) ou `const` (constante). Éviter `var` pour des raisons de portée.
- **Types de données** :
  - Primitifs : string ("texte"), number (42), boolean (true/false), null, undefined.
  - Objets : object ({ clé: valeur }), array ([1, 2, 3]).
- **Opérateurs** : Arithmétiques (+, -, *, /, %), comparaison (==, ===, >, <), logique (&&, ||, !).
- **Structures de contrôle** :
  - Conditionnelles : `if (condition) { ... } else { ... }`, `switch`.
  - Boucles : `for (let i = 0; i < 10; i++) { ... }`, `while`, `do...while`.
  - Boucles sur tableaux : `for...of`, `forEach`.
- **Fonctions** : Déclarées avec `function nom() { ... }` ou fléchées `() => { ... }`.
- **Portée** : Globale, fonctionnelle, de bloc (avec `let` et `const`).
- **Tableaux et objets** : Création, accès (array[0], obj.clé), méthodes (push, pop pour tableaux ; Object.keys pour objets).
- **Chaînage** : Combiner méthodes comme `array.filter(...).map(...)`.
- **Gestion des erreurs** : `try...catch`.
- **Commentaires** : `// Ligne` ou `/* Bloc */`.

---

## 4. HTML Sémantique
- Le **HTML sémantique** consiste à utiliser des balises qui ont un sens clair. En effet, celles-ci décrivent la SIGNIFICATION du contenu, pas seulement son apparence.
- Exemples :
  - `<header>` : en-tête de la page ou de section
  - `<nav>` : barre de navigation
  - `<main>` : contenu principal UNIQUE à la page
  - `<article>` : contenu autonome (blog, actualité, produit, ...)
  - `<section>` : Regroupement thématique
  - `<aside>` : Contenu complémentaire (sidebar)
  - `<footer>` : pied de page

Exemple :
```html
<head>
    <meta charset="UTF-8">
    <title>Mon Blog Sémantique</title>
</head>
<body>
    <header>
        <h1>Mon Blog Développement Web</h1>
        <nav aria-label="Navigation principale">
            <ul>
                <li><a href="#accueil">Accueil</a></li>
                <li><a href="#articles">Articles</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <article>
            <header>
                <h2>Comprendre le HTML Sémantique</h2>
                <time datetime="2024-01-15">15 janvier 2024</time>
            </header>
            
            <section>
                <h3>Introduction</h3>
                <p>Le HTML sémantique change la façon dont nous structurons nos pages...</p>
            </section>
            
            <figure>
                <img src="schema-html.jpg" alt="Schéma expliquant la structure HTML sémantique">
                <figcaption>Structure sémantique d'une page web</figcaption>
            </figure>
        </article>
    </main>
    
    <aside>
        <h3>Articles similaires</h3>
        <ul>
            <li><a href="#">CSS Grid vs Flexbox</a></li>
        </ul>
    </aside>
    
    <footer>
        <p>&copy; 2024 Mon Blog. Tous droits réservés.</p>
    </footer>
```

---

## 5. Mise en page CSS : Flexbox et Grid

### 5.1. Flexbox — explication détaillée

Flexbox (**Flexible Box Layout**) est un système de disposition **unidimensionnel**. Cela signifie qu'il organise les éléments soit en **ligne** (horizontalement), soit en **colonne** (verticalement).

#### 5.1.1. Activation de Flexbox
Pour utiliser Flexbox, il faut définir `display: flex;` sur le conteneur parent :
```css
.container {
  display: flex;
}
```
Les enfants de `.container` deviennent automatiquement des **éléments flexibles**.

#### 4.1.2. Propriétés principales du conteneur Flexbox
- **flex-direction** : définit l'axe principal (ligne ou colonne).
  - `row` (par défaut) → les éléments s'affichent en ligne.
  - `column` → les éléments s'affichent en colonne.
```css
.container { flex-direction: row; } /* horizontal */
.container { flex-direction: column; } /* vertical */
```

- **justify-content** : aligne les éléments sur l'axe principal (horizontal si `row`, vertical si `column`).
  - `flex-start` (par défaut) : alignés au début.
  - `flex-end` : alignés à la fin.
  - `center` : centrés.
  - `space-between` : espaces égaux entre les éléments.
  - `space-around` : espaces égaux autour des éléments.
  - `space-evenly` : espaces strictement égaux.

- **align-items** : aligne les éléments sur l'axe transversal (perpendiculaire à `flex-direction`).
  - `stretch` (par défaut) : s'étirent pour remplir l'espace.
  - `flex-start` : alignés en haut.
  - `flex-end` : alignés en bas.
  - `center` : centrés.

- **gap** : espace entre les éléments.
```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  gap: 20px;
}
```

#### 5.1.3. Propriétés principales des enfants (items Flexbox)
- **flex-grow** : capacité d'un élément à s'agrandir.
- **flex-shrink** : capacité d'un élément à rétrécir.
- **flex-basis** : taille initiale de l'élément.
- **order** : ordre d'affichage (par défaut = 0, plus petit → affiché en premier).

Exemple :
```css
.item1 { flex: 1; }      /* prend l'espace restant */
.item2 { flex: 2; }      /* prend deux fois plus d'espace */
.item3 { flex-basis: 200px; } /* largeur initiale de 200px */
```

#### 5.1.4. Cas d’utilisation typiques de Flexbox
- Barres de navigation horizontales.
- Centrage vertical/horizontal d'un élément.
- Boutons ou cartes alignés sur une ligne.

---

### 5.2. Grid — explication détaillée

CSS Grid Layout est un système **bidimensionnel** (lignes **et** colonnes). C’est l’outil le plus puissant pour organiser des mises en page complexes.

#### 5.2.1. Activation de Grid
Pour utiliser Grid, il faut définir `display: grid;` sur le conteneur parent :
```css
.grid-container {
  display: grid;
}
```
Les enfants deviennent des **éléments de la grille**.

#### 5.2.2. Définir les colonnes et les lignes
- **grid-template-columns** : définit la structure en colonnes.
- **grid-template-rows** : définit la structure en lignes.

Exemple :
```css
.grid-container {
  display: grid;
  grid-template-columns: 200px 1fr 2fr; /* 3 colonnes */
  grid-template-rows: auto auto;        /* 2 lignes */
  gap: 10px;
}
```
- `px` : taille fixe.
- `fr` : fraction de l’espace disponible.
- `auto` : taille automatique selon le contenu.
- `repeat(n, valeur)` : répète une valeur n fois.
- `minmax(min, max)` : définit une taille minimale et maximale.

Exemple responsive :
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}
```
-->crée autant de colonnes que possible, chaque colonne ayant une largeur min de 200px.

#### 5.2.3. Placement des éléments dans la grille
- **grid-column** : sur quelles colonnes s’étend un élément.
- **grid-row** : sur quelles lignes s’étend un élément.

Exemple :
```css
.item1 {
  grid-column: 1 / 3; /* occupe de la colonne 1 à 2 */
  grid-row: 1;       /* première ligne */
}
```

#### 5.2.4. Cas d’utilisation typiques de Grid
- Mise en page globale d’un site (header, sidebar, main, footer).
- Galeries d’images.
- Tableaux de produits.

---

## 6. JavaScript Moderne (ES6+)

### 6.1. let vs const vs var - Comprendre les différences
```javascript
// VAR - À ÉVITER (portée fonction, hoisting problématique)
function testVar() {
    if (true) {
        var x = 10;
    }
    console.log(x); // 10 - x est accessible !
}

// LET - Portée de bloc
function testLet() {
    if (true) {
        let y = 20;
    }
    console.log(y); // Erreur ! y n'est pas défini
}

// CONST - Portée de bloc, valeur constante
const PI = 3.14159;
// PI = 3.14; // ERREUR - impossible de réassigner

// Mais attention aux objets et tableaux :
const person = { name: "Jean" };
person.name = "Pierre"; // Possible
person = { name: "Paul" }; // Erreur
```
#### Règle d'or :
- Utilisez `const` par défaut
- Utilisez `let` seulement si vous devez réassigner la variable

### 6.2. Fonctions fléchées (Arrow Functions)
```javascript
// Fonction traditionnelle
function addition(a, b) {
    return a + b;
}

// Arrow function équivalente
const addition = (a, b) => {
    return a + b;
};

// Version raccourcie (return implicite)
const addition = (a, b) => a + b;

// Un seul paramètre - parenthèses optionnelles
const carre = x => x * x;

// Aucun paramètre
const direBonjour = () => console.log("Bonjour !");
```

### 3.3. Méthodes de tableau : map, filter, reduce
- **map()** : transforme chaque élément
```javascript
const nombres = [1, 2, 3, 4];

// Créer un nouveau tableau avec chaque élément transformé
const carres = nombres.map(nombre => nombre * nombre);
// [1, 4, 9, 16]

const personnes = [
    { nom: "Alice", age: 25 },
    { nom: "Bob", age: 30 }
];

const noms = personnes.map(personne => personne.nom);
// ["Alice", "Bob"]
```

- **filter()** : filtre les éléments
```javascript
const nombres = [1, 2, 3, 4, 5, 6];

// Garder seulement les nombres pairs
const pairs = nombres.filter(nombre => nombre % 2 === 0);
// [2, 4, 6]

const adultes = personnes.filter(personne => personne.age >= 18);
```

- **reduce()** : réduit un tableau à une seule valeur
```javascript
const nombres = [1, 2, 3, 4];

// Somme de tous les éléments
const somme = nombres.reduce((accumulateur, nombre) => {
    return accumulateur + nombre;
}, 0);
// 10

// Compter les occurrences
const mots = ["pomme", "banane", "pomme", "orange"];
const compteur = mots.reduce((acc, mot) => {
    acc[mot] = (acc[mot] || 0) + 1;
    return acc;
}, {});
// { pomme: 2, banane: 1, orange: 1 }
```

- *Chaînage de méthodes*
```javascript
const produits = [
    { nom: "ordinateur", prix: 1000, categorie: "électronique" },
    { nom: "livre", prix: 20, categorie: "éducation" },
    { nom: "téléphone", prix: 500, categorie: "électronique" }
];

// Prix total des produits électroniques
const prixTotal = produits
    .filter(produit => produit.categorie === "électronique")
    .map(produit => produit.prix)
    .reduce((total, prix) => total + prix, 0);
// 1500
```

---

## 7. Conclusion
- **HTML** → structure du contenu
- **CSS** → mise en forme et mise en page (Flexbox, Grid)
- **JavaScript** → dynamisme et interactions (ES6+)
- L’usage des **bonnes pratiques** (sémantique, code clair) est essentiel.

---

## 8. Consolidation : Catalogue Produits

- **Partie 1** : Créer une page web affichant un **catalogue de produits** avec :
  - **HTML sémantique** : header, main, footer
  - **CSS** : mise en page avec **Grid** et alignement des cartes avec **Flexbox**
  - **JavaScript (ES6)** : utilisation de `filter()` et `reduce()`

---

### Étape 1 : Structure HTML
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Catalogue de Produits</title>
  <link rel="stylesheet" href="style2.css">
</head>
<body>
  <header>
    <h1>Catalogue de Produits</h1>
    <nav aria-label="Navigation principale">
      <ul>
        <li><a href="#accueil">Accueil</a></li>
        <li><a href="#produits">Produits</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section class="controls">
      <button id="filterBtn">Filtrer &lt; 5000 FCFA</button>
      <button id="totalBtn">Prix total</button>
    </section>

    <section class="grid-container" id="productList">
      <article class="card">
        <h2>Ordinateur Portable</h2>
        <p>Prix: 150000 FCFA</p>
        <p>Catégorie: Électronique</p>
      </article>
      <article class="card">
        <h2>Livre de Programmation</h2>
        <p>Prix: 3500 FCFA</p>
        <p>Catégorie: Éducation</p>
      </article>
      <article class="card">
        <h2>Téléphone</h2>
        <p>Prix: 50000 FCFA</p>
        <p>Catégorie: Électronique</p>
      </article>
      <article class="card">
        <h2>Stylo</h2>
        <p>Prix: 100 FCFA</p>
        <p>Catégorie: Éducation</p>
      </article>
      <article class="card">
        <h2>Écouteurs Sans Fil</h2>
        <p>Prix: 5000 FCFA</p>
        <p>Catégorie: Électronique</p>
      </article>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 - Mon Catalogue</p>
  </footer>
</body>
</html>
```

---

### Étape 2 : Mise en page CSS
```css
/* ===== RÉINITIALISATION ET STYLES DE BASE ===== */

/* Supprime les marges et paddings par défaut du navigateur */
html, body {
  height: 100%;  /* Prend toute la hauteur du viewport */
  margin: 0;  /* Supprime la marge par défaut */
  padding: 0;  /* Supprime le padding par défaut */
  font-family: Arial, sans-serif;  /* Police de base */
  background: #f9f9f9;  /* Couleur de fond légère */
}

/* ===== STRUCTURE PRINCIPALE FLEXBOX ===== */

/* Le body utilise Flexbox pour une structure en colonne */
body {
  display: flex;  /* Active Flexbox */
  flex-direction: column;  /* Dispose les enfants en colonne */
  min-height: 100vh;  /* Prend au moins toute la hauteur de l'écran */
}

/* Header et footer ne rétrécissent pas */
header, footer {
  background: darkblue;  /* Fond bleu foncé */
  color: white;  /* Texte blanc */
  text-align: center;  /* Centrage du texte */
  padding: 15px;  /* Espacement intérieur */
  flex-shrink: 0;  /* Empêche le rétrécissement */
}

/* ===== NAVIGATION FLEXBOX ===== */

/* Conteneur de la navigation */
header nav ul {
  display: flex;  /* Active Flexbox pour les liens */
  justify-content: center;  /* Centre horizontalement les liens */
  gap: 20px;  /* Espace de 20px entre chaque lien */
  list-style: none;  /* Supprime les puces de liste */
  padding: 0;  /* Supprime le padding par défaut */
  margin: 10px 0 0 0;  /* Marge supérieure seulement */
}

/* Style des liens de navigation */
header nav ul li a {
  color: white;  /* Texte blanc */
  text-decoration: none;  /* Supprime le soulignement */
  font-size: 1.1em;  /* Taille de police légèrement augmentée */
}

/* Effet au survol des liens */
header nav ul li a:hover {
  text-decoration: underline;  /* Souligne au survol */
}

/* ===== CONTENU PRINCIPAL ===== */

/* Le main prend tout l'espace disponible */
main {
  flex: 1;  /* Prend l'espace restant (pousse le footer en bas) */
  display: flex;  /* Active Flexbox pour ses enfants directs */
  flex-direction: column;  /* Dispose les sections en colonne */
}

/* ===== SECTION DES CONTRÔLES ===== */

.controls {
  display: flex;  /* Dispose les boutons en ligne */
  justify-content: center;  /* Centre les boutons horizontalement */
  gap: 20px;  /* Espace entre les boutons */
  margin: 20px;  /* Marge autour de la section */
  flex-shrink: 0;  /* Empêche le rétrécissement */
}

/* ===== GRILLE DES PRODUITS ===== */

.grid-container {
  display: grid;  /* Active CSS Grid */
  /* Crée des colonnes qui s'adaptent automatiquement */
  /* minmax(200px, 1fr) = colonnes d'au moins 200px, maximum 1 fraction */
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;  /* Espacement entre les cartes */
  padding: 20px;  /* Espacement intérieur */
  width: 100%;  /* Prend toute la largeur disponible */
  box-sizing: border-box;  /* Inclut le padding dans la largeur */
  flex: 1;  /* Prend l'espace disponible */
}

/* ===== CARTES DE PRODUITS ===== */

.card {
  background: white;  /* Fond blanc */
  border: 1px solid #ddd;  /* Bordure grise légère */
  border-radius: 8px;  /* Coins arrondis */
  padding: 15px;  /* Espacement intérieur */
  display: flex;  /* Active Flexbox pour le contenu de la carte */
  flex-direction: column;  /* Dispose le contenu en colonne */
  align-items: center;  /* Centre horizontalement */
  justify-content: space-between;  /* Répartit l'espace verticalement */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);  /* Ombre légère */
  height: 100%;  /* Prend toute la hauteur disponible */
  box-sizing: border-box;  /* Inclut le padding dans la hauteur */
}

/* Effet au survol des cartes */
.card:hover {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);  /* Ombre plus prononcée */
  transform: translateY(-2px);  /* Légère élévation */
  transition: all 0.3s ease;  /* Animation fluide */
}
```

---

### Résultat attendu
- Une page avec un **header** contenant une **barre de navigation**, un **catalogue** en **grid**, et un **footer**.
- Chaque produit est affiché dans une **carte alignée en Flexbox**.
- La barre de navigation utilise **Flexbox** pour un alignement horizontal des liens, avec un style cohérent (couleur blanche, hover souligné).
- La page remplit tout l'espace du viewport (hauteur et largeur) grâce à `min-height: 100vh` et `flex: 1`.

---

### Partie 2 : JavaScript pour le catalogue
- Créez un script JavaScript qui gère une liste de produits sous forme de tableau d'objets. Chaque produit a un nom, un prix et une catégorie. Implémentez les fonctionnalités suivantes en utilisant ES6+ :
  1. Filtrez les produits dont le prix est inférieur à 5000 FCFA en utilisant `filter()`.
  2. Calculez le prix total de tous les produits en utilisant `reduce()`.
  3. Transformez la liste pour obtenir un nouveau tableau contenant seulement les noms des produits en majuscules en utilisant `map()`.
  4. Chaînez les méthodes pour calculer le prix total des produits de la catégorie "électronique".
  5. Utilisez `console.log()` pour afficher les résultats.

- Données initiales :
```javascript
const produits = [
  { nom: "ordinateur", prix: 150000, categorie: "électronique" },
  { nom: "livre", prix: 3500, categorie: "éducation" },
  { nom: "téléphone", prix: 50000, categorie: "électronique" },
  { nom: "stylo", prix: 100, categorie: "éducation" },
  { nom: "écouteurs", prix: 5000, categorie: "électronique" }
];
```

- Solution :
```javascript
// Déclaration du tableau de produits avec const, car il ne sera pas réassigné.
// C'est une bonne pratique pour les constantes.
const produits = [
  { nom: "ordinateur", prix: 150000, categorie: "électronique" },
  { nom: "livre", prix: 3500, categorie: "éducation" },
  { nom: "téléphone", prix: 50000, categorie: "électronique" },
  { nom: "stylo", prix: 100, categorie: "éducation" },
  { nom: "écouteurs", prix: 5000, categorie: "électronique" }
];

// 1. Filtrer les produits < 5000 FCFA : Utilise filter() pour créer un nouveau tableau.
// La fonction fléchée vérifie si le prix est inférieur à 5000.
const produitsMoins5000 = produits.filter(produit => produit.prix < 5000);
// Affiche le résultat : Utilise console.log pour voir le tableau filtré.
console.log("Produits < 5000 FCFA :", produitsMoins5000);

// 2. Prix total : Utilise reduce() pour sommer les prix.
// L'accumulateur commence à 0, et on ajoute le prix de chaque produit.
const prixTotal = produits.reduce((total, produit) => total + produit.prix, 0);
// Affiche le résultat : console.log pour le total calculé.
console.log("Prix total :", prixTotal);

// 3. Noms en majuscules : Utilise map() pour transformer chaque nom.
// toUpperCase() convertit la chaîne en majuscules.
const nomsMajuscules = produits.map(produit => produit.nom.toUpperCase());
// Affiche le résultat : console.log pour le nouveau tableau de noms.
console.log("Noms en majuscules :", nomsMajuscules);

// 4. Chaînage pour prix total électronique : Filtre d'abord par catégorie,
// puis map() pour extraire les prix, enfin reduce() pour sommer.
// Tout en une chaîne de méthodes pour plus d'efficacité.
const prixTotalElectronique = produits
  .filter(produit => produit.categorie === "électronique")
  .map(produit => produit.prix)
  .reduce((total, prix) => total + prix, 0);
// Affiche le résultat : console.log pour le total spécifique.
console.log("Prix total électronique :", prixTotalElectronique);
```

> # ANNEXE

Les formulaires HTML permettent de **recueillir des informations**
auprès des utilisateurs : texte, choix, fichiers, etc.\
Ils sont essentiels pour de nombreuses fonctionnalités : connexion,
inscription, recherche, paiement en ligne, etc.


## 1. Structure de base d'un formulaire

Un formulaire est défini par la balise `<form>` :

``` html
<form action="/traitement" method="post">
  <!-- Les champs du formulaire ici -->
</form>
```

-   **`action`** : définit l'URL où les données seront envoyées.\
-   **`method`** : précise la méthode d'envoi :
    -   `get` : les données apparaissent dans l'URL (`?nom=valeur`).\
    -   `post` : les données sont envoyées dans le corps de la requête
        (plus sûr).

------------------------------------------------------------------------

## 2. Les principaux champs de formulaire

### a) Le champ texte

``` html
<input type="text" name="nom" placeholder="Votre nom">
```

### b) Le champ mot de passe

``` html
<input type="password" name="motdepasse">
```

### c) Le champ email

``` html
<input type="email" name="email">
```

### d) Zone de texte multi-lignes

``` html
<textarea name="message" rows="5" cols="30"></textarea>
```

### e) Cases à cocher

``` html
<input type="checkbox" name="newsletter" value="oui"> S’abonner à la newsletter
```

### f) Boutons radio

``` html
<input type="radio" name="genre" value="homme"> Homme
<input type="radio" name="genre" value="femme"> Femme
```

### g) Listes déroulantes

``` html
<select name="pays">
  <option value="cm">Cameroun</option>
  <option value="fr">France</option>
  <option value="ca">Canada</option>
</select>
```

### h) Sélection de fichier

``` html
<input type="file" name="cv">
```

### i) Boutons

``` html
<input type="submit" value="Envoyer">
<input type="reset" value="Réinitialiser">
<button type="button">Un simple bouton</button>
```

------------------------------------------------------------------------

## 3. Les attributs importants

-   **`name`** : clé envoyée au serveur.\
-   **`value`** : valeur envoyée.\
-   **`id`** : identifiant unique, souvent lié à un `<label>`.\
-   **`placeholder`** : texte indicatif.\
-   **`required`** : rend le champ obligatoire.\
-   **`readonly`** : champ non modifiable mais visible.\
-   **`disabled`** : champ désactivé (non envoyé).\
-   **`maxlength` / `minlength`** : limite de caractères.\
-   **`min` / `max` / `step`** : pour les nombres et dates.

------------------------------------------------------------------------

## 4. Associer des labels aux champs

``` html
<label for="email">Votre email :</label>
<input type="email" id="email" name="email">
```

------------------------------------------------------------------------

## 5. Regrouper des champs : `<fieldset>` et `<legend>`

``` html
<fieldset>
  <legend>Informations personnelles</legend>
  <label for="nom">Nom :</label>
  <input type="text" id="nom" name="nom">
  
  <label for="prenom">Prénom :</label>
  <input type="text" id="prenom" name="prenom">
</fieldset>
```

------------------------------------------------------------------------

## 6. Types d'`<input>` disponibles (HTML5)

-   `text`, `password`, `email`, `url`, `tel`, `search`
-   `number`
-   `date`, `time`, `month`, `week`, `datetime-local`
-   `range`
-   `color`
-   `file`
-   `checkbox`, `radio`
-   `hidden`
-   `submit`, `reset`, `button`

------------------------------------------------------------------------

## 7. Validation HTML

-   `required`\
-   `type="email"`\
-   `pattern="[0-9]{5}"`\
-   `min`, `max`, `step`\
-   `maxlength` / `minlength`

------------------------------------------------------------------------

## 8. Attributs de `<form>`

-   `action`\
-   `method`\
-   `enctype`\
-   `autocomplete`\
-   `novalidate`\
-   `target`

------------------------------------------------------------------------

## 9. Exemple complet de formulaire

``` html
<form action="/inscription" method="post" enctype="multipart/form-data">
  <fieldset>
    <legend>Informations personnelles</legend>

    <label for="nom">Nom :</label>
    <input type="text" id="nom" name="nom" required>

    <label for="email">Email :</label>
    <input type="email" id="email" name="email" required>

    <label for="mdp">Mot de passe :</label>
    <input type="password" id="mdp" name="mdp" minlength="8" required>
  </fieldset>

  <fieldset>
    <legend>Préférences</legend>
    <label>
      <input type="checkbox" name="newsletter" value="oui"> Recevoir la newsletter
    </label>
    <label for="pays">Pays :</label>
    <select name="pays" id="pays">
      <option value="cm">Cameroun</option>
      <option value="fr">France</option>
      <option value="ca">Canada</option>
    </select>
  </fieldset>

  <fieldset>
    <legend>Photo de profil</legend>
    <input type="file" name="avatar" accept="image/*">
  </fieldset>

  <button type="submit">S’inscrire</button>
  <button type="reset">Annuler</button>
</form>
```

------------------------------------------------------------------------

## 10. Exercices

1.  Crée un formulaire de **connexion** avec email et mot de passe.\
2.  Crée un formulaire de **recherche** avec `method="get"`.\
3.  Crée un formulaire d'**inscription** complet (nom, prénom, date de
    naissance, genre, pays, newsletter).\
4.  Ajoute un champ `code postal` validé avec `pattern`.\
5.  Crée un formulaire d'upload de fichier CV.

------------------------------------------------------------------------

## Conclusion

Les formulaires HTML sont composés de champs (`input`, `textarea`,
`select`) organisés dans `<form>`.\
Ils permettent de collecter et d'envoyer des données.\
Avec HTML5, on dispose de validations automatiques et de nouveaux types
de champs.\
Un bon formulaire doit être clair, accessible, et validé **côté
serveur** pour la sécurité.
