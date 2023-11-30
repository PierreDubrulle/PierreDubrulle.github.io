---
categories: [data, bash]
tags: [linux, data, tail, cli, head]

# Optimiser la Manipulation de Données avec Bash : Une Approche Holistique
___
## Partie 1: Exploration de Données avec les Commandes cat, head, tail, et Notions de Redirection

__*Par Pierre Dubrulle*__


---
## Introduction
Les commandes cat, head, et tail sont des outils fondamentaux pour explorer le contenu des fichiers texte en ligne de commande. Combinées avec des techniques de redirection, elles deviennent encore plus puissantes pour manipuler et analyser les données. Examions également comment enchaîner ces commandes pour effectuer des tâches plus complexes.

Pour tous les exemples nous utiliserons un dataset répertoriant les différents sets [Lego](https://www.kaggle.com/datasets/willianoliveiragibin/lego-sets-and).

## Pré-requis

Il est nécessaire d'avoir accès à un environnement Linux donc soit sur une machine avec un os Linux soit via WSL.

---

## 1. Commande `cat`
La commande `cat` est utilisée pour afficher le contenu complet d'un fichier.
### Syntaxe de base
```bash
cat fichier
```
- **`fichier`**: Le nom du fichier dont on souhaite afficher le contenu.
Cette commande affichera la totalité du contenu du fichier.

## 2. Commande `head`
La commande `head` est utilisée pour afficher les premières lignes d'un fichier.
### Syntaxe de base
```bash
head fichier
```
### Exemple pratique
En utilisant le fichier répertoriant les sets Lego, on peut afficher les 20 premières lignes avec la commande suivante:
```bash
head -n 20 sets.csv
```
<img src="{{ "assets/gifs/head.gif" | prepend: site.url}}" alt="head exemple" />
<!-- ![Exemple head](/_posts/gifs/head.gif) -->
Par défaut la commande `head` renverra les 10 premières lignes.

## 3. Commande `tail`
La commande `tail` est utilisée pour afficher les dernières lignes d'un fichier.
Elle s'utilise de la même façon que la commande `head`.

### Syntaxe de base
```bash
tail fichier.csv
```
<img src="{{ "assets/gifs/tail.gif" | prepend: site.url}}" alt="tail exemple" />
<!-- ![Exemple tail](/_posts/gifs/tail.gif) -->

## 4. Notions de redirection
La redirection en Bash permet de rediriger la sortie standard (stdout) ou l'entrée standard (stdin) d'une commande vers un fichier ou depuis un fichier.

- `>` : Redirige la sortie standard vers un fichier (crée ou remplace le fichier).
```bash
head fichier > fichier_sortie
```
- `>>` : Redirige la sortie standard vers un fichier en ajoutant au contenu existant (crée le fichier s'il n'existe pas).
```bash
tail -n 50 fichier >> fichier_sotie
```

### Exemple pratique
Supposons qu'on possède deux fichiers:
- Le fichier **sets.csv** qui contient les données pour les sets Lego jusqu'en 2020,
- Le fichier **sets2.csv** qui contient les mêmes données mais pour la période 2021-2022.

On souhaite avoir un seul fichier contenant l'ensemble des données. Ainsi, avec les commandes abordées dans cet article on peut utiliser la ligne de commande suivante:
```bash
cat sets.csv sets2.csv > full_sets.csv
```
**Explication**:
La commande `cat` va afficher à l'écran le contenu des deux fichiers et l'opérateur `>` va écrire la sortie de la commande `cat` dans le fichier *full_sets.csv*.
Attention, si le fichier **sets2.csv** contient aussi une ligne avec les noms des colonnes cette ligne se trouvera deux fois dans le fichier final. Nous verrons comment mitiger ce problème dans un autre article ...

![Gif suspense](https://media.giphy.com/media/y0SJVYxf90J1u/giphy.gif)

## Conclusion
Les commandes cat, head, et tail sont des outils de base pour explorer le contenu des fichiers texte. Combinées avec les notions de redirection, elles deviennent des instruments puissants pour manipuler et analyser les données. En comprenant comment chaîner ces commandes et les utiliser avec la redirection, vous pouvez accomplir des tâches plus complexes et effectuer une exploration de données efficace en ligne de commande.

Rendez-vous la semaine prochaine pour un autre article sur la manipulation des données.