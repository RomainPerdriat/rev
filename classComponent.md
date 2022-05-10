## Définition: 
Un classComponent est un composant React, ecrit en classe donc suivant les principes de la poo. 
Pour en créer un il faut d'abord hériter de React.Component

```jsx

    class MaClasse extends React.Component{

        render (){
            return(
                <h1>Contenu a afficher</h1>
            );
        }
    }
    export default MaClasse

```
Pour retourner du jsx dans un classComponent j'ai besoin de la fonction `render`,  (alors que dans un functionComponent, un render simple suffit).

Pour qu'il puisse hériter de React.Component, un classComponent a besoin d'un constructor : 

```jsx

     constructor(props) {
    super(props); // super est la fonction qui permet que mon instance hérite des propriétés de classe
  }
```
Ce constructor se place au plus haut dans ma classe

Maintenant dans mon instance de classe,si je veux utiliser/récupérer une props, je devrais faire : ` this.props.nomDeLaProps`, this faisant référence à mon instance.

Si je souhaite utiliser this dans une fonction de handle, il me faudra attache le contexte de mon instance à ma fonction de handle, pour cela deux solutions: 

A chaque fonction je rajouter `bind()` : 

```jsx
class MaClass extends React.Component {
  handleClick() {
    console.log(`I've been click`, this);
  }

  render() {
    const { name } = this.props;

    return (
      <li
        onClick={this.handleClick.bind(this)} // <=== Ici j'attache mon contexte
      >
        {name}
      </li>
    );
  }
}
```

Mais en faisant comme ça je suis obligé de le répéter à chaque fonction. A la place je peux directement dans mon constructor "binder" mon this : 


```jsx
class MaClass extends React.Component {

    constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick(event) {
    console.log(`I've been click`, event);
  }
  render() {
    const { name } = this.props;
    return (
      <li
        onClick={this.handleClick} //<== Maintenant je ne rattache plus avec bind puisqu'il est définit dans mon constructor
        {name}
      </li>
    );
  }
}
```
 ## Création et utilisation du state en classComp:

 Dans mon constructor, je crée le state :  

 ```js
  constructor(props) {
    super(props); 


    this.state = {
      foo: 'bar',
    };
  }
```

Je peux maintenant accéder à ce state partout dans mon classComponent en faisant : `this.state.foo`

Si je souhaite maitenant mettre à jour ce state, je devrais utiliser  `setState`. 

```jsx
this.setState({
foo: 'plusbar'
});

```
Si je souhaite m'appuyer sur une ancienne valeur de foo je vais utiliser oldState : 
```jsx

this.setState((oldState, props) => {
      return {
          a: oldState.a * 2
      };
  });

```

