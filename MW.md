# Les MiddleWares:

## 1 Pourquoi faire ?

L'intérêt des MiddleWares (MW) est qu'ils servent à intercepter une info, avant qu'elle n'arrive dans le reducer. En interceptant cette info, on peut lui appliquer des modifications 'à la volée'. On peut donc s'en servir pour : 

- filtrer des actions

- ajouter du debug

- lancer un compte à rebours

- lancer une ou des actions en fonction d'une activité

On se sert de MW car, on pourrait trés bien faire notre requete dans le containers, mais pour la SOC et  pour que chaque entité est un rôle propre et restreint on préferera l'usage des MW.


Un MW est effectué à chaque fois qu'un `dispatch` est fait.

Leur usage est en fait similaire aux `UseEffect` des fonctions components sauf qu'on le fait dans un fichier à part, c'est donc plus propre et réutilisable partout.

### Il faut retenir que depuis un MW: 

  - On a accès au store
  - On peut donc y faire des dispatch
  - On peut aussi y faire des getState()
  

Pour se faire il  faut se rappeler de faire `store.cequejeveux`. Exemple : `store.dispatch()`

Petit rappel , il est impossbile de modifier le store directement, on est obligé de passer par la méthode dispatch().

## 2 Syntaxe et fonctionnement : 

La syntaxe d'un MW basique est toujours la même : 

```js
const monMW = (store) => (next) => (action) => {
    console.log('Mon MW', action);
    next(action); 
  }; 
  export default monMW
```

Dans ce code , la seule chose qui est amenée à changé ce sera le nom de la fonction, la syntaxe reste la même tout le temps.

Une fois fait il faudra bien penser à l'importer dans notre index.js du store, comme ça il sera utilisable partout, ici encore la syntaxe est typique : 
```js
 //syntaxe type pour ajouter un MW au niveau de l'index du store
import { createStore, applyMiddleware, compose } from 'redux'; 
import reducer from 'src/reducers'; 

// on importe les middlewares 
import monMW from 'src/middlewares/monMW'; <=================
import ajax from 'src/middlewares/ajax'; 

// on met bout à bout tous nos middlewares 
const middlewares = applyMiddleware(debug, ajax); 

// on met bout à bout le redux devtools et nos middlewares 
// https://github.com/zalmoxisus/redux-devtools-extension#12-advanced-store-setup 
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose; 
const enhancers = composeEnhancers(middlewares); 

// on crée le store à qui l'on passe le reducer et les middlewares (avec le devtool) 
const store = createStore(reducer, enhancers); 

export default store;
```

Ce code peut être copié/collé en adaptant bien sur le nom et sources des MW.


## 3 Attribuer une action  à mon MW:

Dans mon dossier actions, je vais définir l'action que je veux qu'éxecute mon MW.

```js
export const MON_ACTION = 'MON_ACTION';


export function actionMonAction() {
  return { type: MON_ACTION};
}
```

Je pense ensuite à importer mon action dans mon MW et je lui applique ce que je veux, par exemple : 

```js
if (action.type === MON_ACTION) { console.log(`coucou`)}    
    return;
```
Maintenant que j'ai pus tester que ça marche je peux mettre toute ma requête dans mon MW.

ICI EXEMPLE DU COURS AVEC LE SUBMIT_LOGIN :
 ```js

import { SUBMIT_LOGIN } from 'src/actions/settingsActions';
import { requestLogin } from 'src/requests/login';
import * as actions from 'src/actions';

const middlewareLogin = (store) => (next) => async (action) => {
  if (action.type === SUBMIT_LOGIN) {
    // on fait içi le code de tout la requete de login
    const state = store.getState();
    // es6: const { settings: { mail, password } } = store.getState();

    const response = await requestLogin(
      state.settings.mail, state.settings.password,
    );
    console.log(response);

    // si on a pas d'erreur dans notre post /login
    if (response.status === 200) {
      // SET IS CONNECTED
      store.dispatch(
        actions.actionSetIsConnected(true),
      );
      // SET PSEUDO
      store.dispatch(
        actions.actionSetPseudo(response.data.pseudo),
      );
      // CLOSE FORM LOGIN
      store.dispatch(
        actions.actionSetIsOpen(false),
      );
    }
    return;
    // on ne passe pas l'action SUBMIT_LOGIN à la suite, elle est interrompu
  }

  next(action); // permet de passer l'action à la suite: soit le prochain middleware, soit les reducers
};

export default middlewareLogin;

 ```

Et maintenant donc mon Containers (setting en l'occurence), je n'ai plus qu'a faire :

```js
const handleSubmit = async () => {
    dispatch(
      actions.actionSubmitLogin(),
    );
  };

```

ATTENTION: Dans le code ci-dessus on passe par `actions`, qui est déclaré comme un alias ligne 97. Par contre le `action.type` de la ligne 100 fait référence au `action` de la ligne 99.


lE CHEMIN EST LE SUIVANT: JE DEFINIT MON ACTION, ELLE EST PASSÉ AU MW QUI L'ENVOIE ENSUITE DANS LE REDUCER. CE DERNIER AGIT EN FONCTION DE L'ACTION RECU