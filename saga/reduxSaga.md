## Pourquoi faire? 

Imaginons que je veuille sauvegarder une donnée en base au click. Contrairement à si je n'avais pas de serveur (mon state serait modifié directement dans le front),là, il faut que mon action soit sauvegardée en base. Comme cette démarche est asynchrone, je ne sais pas combien de temps cela va prendre et il ne faudrait pas que mon changement de state passe par le reducer avant que je n'ai reçu ma réponse de l'api, je ne veux pas update mon state front avant mon ajout en base.
C'est la que saga intervient . 

## Les etapes 
 L'idée de saga est donc de mettre en place un observateur qui va intercepter une tache et qui en executera les etapes une par une, pour ne pas créer d'effet de bords.

### 1 

Dabord je fais un `yarn add redux-saga`.

### 2 index.js

Dans mon index j'importe : 
`import createSagaMiddleware from 'redux-saga' ;`

`const sagaMiddleware = createSagaMiddleware();`

Maintenant je peux passer à mon store via applyMiddleware mon nouveau MW:

`const store = createStore(reducer, applyMiddleware(sagaMiddleware));`

### 3 sagas.js

Je crée un fichier appelé saga.js
Dans celui-ci je peux créer mon watcher qui va regarder tous les dispatch. 

```js
import { takeLatest, put } from 'redux-saga/effects';
import { delay } from "redux-saga";
export function* watchAgeUp(){
    yield takeLatest('AGE_UP', ageUpAsync)
}

export function* ageUpAsync(){
    yield delay(4000)
    yield put({'AGE_UP_ASYNC', value : 1})
}
```

Donc ici j'observe, au moment ou j'intercepte un AGE_UP,je met sur pause et j'execute ma fonction ageUpAsync . 
Dans cette fonction que se passe-t-il? 
J'arrive, je met sur pause pendant 4sc puis j'envoie ma seconde action (la première n'est toujours pas arrivé dans le reducer puisque j'utilise saga). 
Quang AGE_UP_ASYNC sera résolu je pourrai "enlever la pause" de watchAgeUp.

### 4 index.js
Je n'ai maintenant plus qu'a importer ma fonction watchAgeUp et à la passer à mon sagaMiddleWare
`sagaMiddleWare.run(watchAgeUp);`

### Notes 

On a pour habitude de séparer les sagas en deux rôles : les watchers et les workers.

#### watchers :  

Les watchers sont la pour observer toutes les actions dispatchées dans le store puis une fois attrapées, ils les déléguent aux workers.  

#### workers :

Ils receptionnent les actions interceptées par les workers et effectuent une action dessus.