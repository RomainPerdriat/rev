## ForEach :

Je veux parcourir un tableau d'objet de personnage

```js

array.forEach(element => {
    console.log(element.nom);
})

```

## .map :

Convertit un tableau en un second tableau
```js

let persos = tabPersonnages.map(element => {
    return element.nom
} )

console.log(persos) ===> nomDesPersos

```

Pour récupérer le prix des éléments en y appliquant une remise de 30%, il me suffit de faire : 

```js
let reduction = tabPersonnages.map(element => {
    return element.prix - 0.3 * element.prix
} )
```
## Filter :

Permet de réaliser un filtre sur un tableau pour ne récupérer que certains elements.
ici je veux filter tout les personnages dont la puissance est supérieur à 150.

```js

let puissants =  tableauPersonnages.filter(element => {
    return element.puissance > 150
})
```

## Find :

Permet de trouver une valeur précise dans un tableau.

```js

let achille = tableauPersonnage.find(element => {
    return element.name === "Achille"
})
```

En faisant ainsi je récupère l'objet Achille dans son intégralité, avec le reste des propriétés.

## Some  :
 Cette méthode renvoie true ou false si des elements répondent à la condition demandée
 Dans le cas présent permet de vérifier si il y a des elemetns dont le prix dépasse les 6000.

```js

let cher = tableauPersonnages.some(element => return element.prix > 6000)

```
ici un console log me renverra true si des figurines ont un prix supérieur à 6000 et false si ce n'est pas le cas.


## Every :

Elle renvoie true si tout les elements du tableau respectent une certaine condition

```js

let  ensembleFort = tableauPersonnages.every (element => {
    return element.puissance > 10000
})
```
Si c'est vrai alors ca me retourne true sinon false.

## Reduce : 
Permet de faire une opération sur un tableau et de renvoyer une combinaison des opérations.

```js

let somme prix = tableauxPersonnage.reduce((accumulateur, element)=> {
    return accumulateur + element.prix
},0)
```
Le zero correspond à la valeur de départ.
L'accumulateur est le cumul de before et now alors que element est la valeur de now (qui viendra s'ajouter au futur accumulateur)

## Include

Ne prend pas de fonction mais un simple argument.


```js

let notes = [1,5,14,20];
let estPresent = notes.includes(20);
console.log(estPresent)
```

Ici va me retourner true alors que si je met 13  va me retourner false.
