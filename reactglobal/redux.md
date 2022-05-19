### Redux

Redux me permet de stocker dans un même endroit mes variables globales; il faut entendre par là celles qui ont une influence sur d'autre composants que le leur.

### Reducer
Le reducer lui  va recevoir nos actions et modifier le state en fonction d'elle.
En fait le reducer c'est un ensemble de fonctions qui reçoit la donnée à modifier et comment la modifier. Il crée une copie de la donnée et la retourne.
Mes composants lisent les actions du stores en faisant des getState (fonction qui permet d'accéder aux états contenus dans le store.)

### Action

Une action c'est un objet qui contient un type (c'est le façon de l'indentifier, disons que c'est son prénom), on la passe au reducer comme cela : `store.dispatch({type: "nomDeMonAction"})`. Une action prend aussi un payload, c'est en fait un contenu qu'elle va donner au reducer pour qu'il puisse modifier le state en question.

Dans mon dossier action généralement on définit un action creator : 
`export const SET_STATE = 'SET_STATE'`
Ca permet d'avoir tout mes actions au même endroit.

### React-Redux:

Cette biblio me permet d'abonner tout mes composants au store (donc aux states); elle va gérer les abonnements.
Dans mon composant le plus haut je fais fournir mon store, ainsi en l'englobant, je suis sur qu'il soit diffusé partout : 
```jsx
    const rootReactElement = (
  <Provider store={store}>
    <App />
  </Provider>
);
```

Maintenant je dois relier mes composants au store; pour ce faire je peux utiliser les hooks de redux : useSelector et useDispatch: 
`import { useSelector, useDispatch } from 'react-redux';`

useSelector  me permet de lire les informations du state:
    `const prenom = useSelector((state)=state.prenom)`

 tandis que useDispatch va me permettre d'utiliser dispathc dans mon composant

 ```jsx
 const dispatch = useDispatch (); 
  const handleClick = () => {
    dispatch(select());
  };
 ```

 Donc ici j'envoie dans mon reducer la fonction select lorsque je click sur le bouton.



 