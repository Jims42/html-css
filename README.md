# html-css

# GRID

En CSS Grid, **`1fr` (pour fraction unit, ou unité de fraction) représente une fraction de l'espace disponible dans la grille.
```css
grid-template-columns: repeat(4, 1fr);
````

Dans ton exemple `repeat(4, 1fr)`, tu demandes à ton conteneur de créer 4 colonnes de taille égale, qui vont se partager équitablement tout l'espace disponible en largeur. Si ton conteneur fait 800px de large, chaque colonne fera 200px. Si la taille de la fenêtre change, les colonnes s'ajustent automatiquement pour garder des proportions égales.


Si tu écris:
```css
 grid-template-columns: repeat(4, auto);
 ````
 , le comportement change radicalement :

Largeur basée sur le contenu : Chaque colonne s'adapte automatiquement pour prendre uniquement la largeur de son contenu (le texte ou les éléments qu'elle contient).

Répartition inégale : Si la première colonne a un mot court et la deuxième une longue phrase, la deuxième sera beaucoup plus large.

Pas de remplissage forcé : Si le contenu total ne remplit pas toute la largeur du conteneur, il restera de l'espace vide à droite.

## En résumé :

* Utilise 1fr quand tu veux des colonnes régulières et proportionnelles qui occupent tout l'espace.

* Utilise auto quand tu veux que la taille des colonnes s'adapte au millimètre près à ce qu'elles contiennent.

## auto sans repeat

```css
grid-template-columns: auto 1fr;
`````
Cette ligne crée deux colonnes bien distinctes :

* auto (la première colonne) : Elle s'adapte exactement à la taille de ce qu'elle contient (par exemple, un menu latéral ou une image).

* 1fr (la deuxième colonne) : Elle prend tout le reste de l'espace disponible sur la ligne.

C'est une disposition très pratique et très utilisée pour faire des layouts avec une barre latérale fixe (en taille de contenu) et une zone principale qui s'étire !

```css
grid-template-columns: 1fr auto;
````
* La première colonne (1fr) prend tout l'espace disponible qu'elle peut.

* La deuxième colonne (auto) se réduit au minimum pour s'adapter uniquement à la taille de son contenu.

C'est très utile si tu veux que ta zone principale prenne toute la place et que ton élément de droite (par exemple, un bouton ou une petite icône) garde juste la taille nécessaire.

## Responsive
```css
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
````
C'est l'une des lignes de code les plus puissantes et magiques en CSS Grid ! Elle permet de créer une grille entièrement responsive et automatique, sans avoir à utiliser la moindre media query (@media).

### 1. Décortiquons la formule
* `auto-fit` : Le navigateur calcule tout seul combien de colonnes peuvent tenir côte à côte dans le conteneur, et il ajuste le nombre de colonnes en temps réel quand tu redimensionnes la fenêtre.

* `minmax(200px, 1fr)` : C'est la taille que chaque colonne peut prendre :

    * `min` (minimum = 200px) : Une colonne ne pourra jamais descendre en dessous de 200px de large.

    * `max` (maximum = 1fr) : S'il reste de la place, la colonne s'étire et grandit pour occuper l'espace disponible.
### 2. Le résultat visuel en action
* Sur un grand écran (ordinateur) : Le navigateur fait entrer le maximum de colonnes de 200px (ou plus si elles s'étirent). Si tu as 4 éléments, ils se mettent sur une seule ligne.

* Sur un écran moyen (tablette) : La grille se réorganise. S'il n'y a plus la place pour 4 colonnes, elle passe à 3, puis à 2.

* Sur un petit écran (téléphone) : Les colonnes passent automatiquement l'une sous l'autre pour faire 100% de large (chacune faisant au moins ses 200px ou s'adaptant à l'écran).
### En résumé : 
C'est le $${\color{green}\text{mot}}$$ cheat-code ultime pour faire des galeries d'images ou des listes de cartes (comme des cartes de produits sur un site e-commerce) qui s'adaptent à n'importe quel écran comme par magie.