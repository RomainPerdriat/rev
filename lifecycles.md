
## Les phases :

Naissance : mount
Vie/evolutions : update
Mort : unmount

Lors de la naissance, le constructor est appelé, on attache les props et le state à l'instance
Ensuite on appel le render, c'est la phase ou l'on crée l'élément en fonction de la phase précédente
Enfin on appel ComponentDidMount qui signifie la fin de la naissance du Comp

Ensuite pour chaque modification que je souhaiterai effectuer sur mon composant, je vais passer par la phase de vie, en gros à chaque changement de state
ou de props, un nouveau render sera fait et la méthode componentDidupdate sera appellée.

Utilisations : 

```jsx

    componentDidMount(){
        console.log(`Composant tout neuf`)
    };

    componentDidUpdate() {
        console.log(`Le composant à bien été modifié`)
    };
```

Attention, lors de l'usage de React.PureComponent qui s'occupe d'optimiser le rendu (ne le fait que si les props et states changent).
En effet la comparaison effectué pour savoir s'il y a eu des changements est une comparaison de surface et non pas de profondeur. Donc si le contenu de mes props ou state a changé mais pas leur nom, lorsque React va "survoler" mes tableaux ou objets, il va se rendre compte que les boites sont les mêmes d'extérieur, mais comme il ne les ouvre pas il ne voit pas que le contenu à changer, d'où l'intéret de créer un new tableau avec l'aide du spread operator.