# Leçon 9 : Stratégies de Branches (Workflows)

Savoir créer des branches, c'est bien. Savoir les organiser dans un workflow cohérent pour toute une équipe, c'est mieux. Une stratégie de branches (ou workflow) est un ensemble de règles et de conventions qu'une équipe suit pour utiliser Git. Cela évite le chaos et rend le projet plus facile à maintenir.

Nous allons voir deux des stratégies les plus populaires.

## 1. GitHub Flow (Le plus simple et le plus courant)

Popularisé par GitHub, ce workflow est extrêmement simple et efficace, particulièrement pour les projets web ou les applications qui sont déployés en continu.

### Les principes clés :

1.  **Tout ce qui est dans la branche `main` (ou `master`) est déployable.** C'est la règle d'or. La branche `main` doit toujours être stable et prête à être mise en production.

2.  **Pour travailler sur quelque chose de nouveau, créez une branche descriptive depuis `main`.** Le nom de la branche doit être explicite (ex: `feature/add-login-page`, `fix/wrong-color-button`).

3.  **Poussez votre branche sur le dépôt distant régulièrement.** Cela permet de sauvegarder votre travail et de le rendre visible aux autres.

4.  **Ouvrez une Pull Request (PR) quand vous avez besoin d'avis ou que votre travail est prêt.** La PR est l'outil central de la revue de code et de la discussion.

5.  **Fusionnez (merge) la PR dans `main` uniquement après son approbation.**

6.  **Une fois fusionnée, la branche est immédiatement déployée en production.**

Ce workflow est très flexible et repose sur des cycles rapides de développement, de revue et de déploiement.

## 2. GitFlow (Le plus structuré)

GitFlow est un modèle plus ancien et beaucoup plus strict. Il est bien adapté aux projets qui ont des cycles de release planifiés (par exemple, une application mobile qui sort une nouvelle version tous les mois) plutôt qu'un déploiement continu.

### Les branches principales :

-   `main` (ou `master`) : Contient l'historique des versions officielles (releases). On ne commite jamais directement dessus. Chaque commit sur `main` est un numéro de version (tag).
-   `develop` : C'est la branche d'intégration principale. Toutes les nouvelles fonctionnalités y sont fusionnées. C'est l'état de la prochaine version à venir.

### Les branches de support :

-   **`feature/*`** : On les crée depuis `develop`. C'est là que les développeurs travaillent sur leurs nouvelles fonctionnalités. Une fois terminées, elles sont fusionnées dans `develop`.
    -   Exemple : `feature/user-profile`

-   **`release/*`** : Quand la branche `develop` contient assez de fonctionnalités pour une nouvelle version, on crée une branche `release` depuis `develop`. Sur cette branche, on ne fait que des corrections de bugs mineurs et on prépare la release (mise à jour du numéro de version, etc.).
    -   Exemple : `release/v1.2.0`

-   **`hotfix/*`** : Si un bug critique est découvert en production (sur `main`), on crée une branche `hotfix` depuis `main`. On corrige le bug, puis on fusionne cette branche à la fois dans `main` (pour mettre à jour la production) ET dans `develop` (pour que le correctif soit inclus dans la prochaine version).
    -   Exemple : `hotfix/critical-login-bug`

### Comparaison

| Aspect | GitHub Flow | GitFlow |
|---|---|---|
| **Complexité** | Très simple | Complexe |
| **Branche principale** | `main` | `main` et `develop` |
| **Idéal pour** | Déploiement continu, projets web | Releases planifiées, applications mobiles/de bureau |
| **Rythme** | Rapide et flexible | Structuré et contrôlé |

Pour la plupart des projets modernes, **GitHub Flow est un excellent point de départ**. Ne vous compliquez la vie avec GitFlow que si votre projet l'exige vraiment.
