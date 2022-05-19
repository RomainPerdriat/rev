
## 1 Objectifs


Avoir les mêmes conventions de nommage pour naviguer facilement entre les différents commits et bien se repérer. 

En effet, avec la commande `git log` on peut avoir accès à l'historique de tous nos commits.

## 2  Les règles

Ce modèle de structure de commit est basé sur les règles d'Angular

Il n'y a pas de bon, ou de mauvais message de co... FAUX!

En lisant un message de commit il faut pouvoir indentifier deux choses : ce qui a changé et pourquoi ça a changé.

Le comment cela a changé n'a pas d'importance car il existe une commande pour cela : `git diff`. 



## 3 Les différentes parties du message:

Le format standard et que nous viserons à atteindre et le suivant :

```
<type>(<portée>): <sujet>

(<description>

<footer>) 
```

Pour faire simple pendant l'Appo et se concentrer sur le reste, je laisse description et footer de côté, à faire valider par l'équipe.

### 3.1 Le type:

Cet élément est **obligatoire** , il nous informe de l'action du code ajouté dans le commit. Ici il faut se demander ce que nous sommes en train de modifier. C'est l'élément le plus important car il va en quelques sortes nous permettre de filtrer nos commits.

`build` : changements qui affectent le système de build ou des dépendances externes (npm par exempleopu des modifs dans le bundler).

`ci` : changements concernant les fichiers et scripts d’intégration ou de configuration (Travis, Ansible, BrowserStack…)
??? A définir mieux.

`feat` : ajout d’une nouvelle fonctionnalité.

`fix` : correction d’un bug.

`perf`: amélioration des performances.

`refactor`: Lorsque l'on refactorise **sans** apporter de nouvelles fonctionnalités ni de performance.

`style` : ici on ne parle que de l'aspect visuel de notre code :indentation, mise en forme, ajout d’espace, renommer une variable… Ici on ne touche **pas** à la logique.

`docs` : rédaction ou mise à jour de documentation.

`test` : ajout ou modification de tests.

`revert`: Annulation d’un précédent commit.

### 3.2 La portée : 
Cet élément est **facultatif**. Il permet de savoir quel élément est affecté par les modifications.
Sagit-il de la partie authentification, de la partie contact ect...?

Exemple de portée : 

`controller`
`route`
`middleware`


### 3.3 Le sujet : 

Cet élément est **obligatoire**. Il contient une descritpion ***rapide*** des changements.

La convention veut qu'on utilise le présent, on mettra change, add, update et non pas changed, added ou updated. On ne met pas de majuscule ni de point.

On reste concis et précis!

Exemple de sujet `add caching for better performance`


## 4 Quelques exemples simples:

`feat(controller): add post's controller `

`fix(controller): use the correct JS code`

`docs(actions): add action add_message documentation`


## 5 Un outil pour respecter la convention:

A voir avec l'équipe si besoin ? Ca peut être assez contraignant donc à voir si niveau contrainte c'est judicieux de se rajouter ça? 

Aller voir en bas de page :

https://www.codeheroes.fr/2020/06/29/git-comment-nommer-ses-branches-et-ses-commits/