## Saga Helpers : 

### takeEvery :

    A chaque fois que X à lieu alors réalise Y .

### takeLatest : 

    Idem que takeEvery sauf que si la dernière action à effectuer est similaire à toutes les autres alors il n'en effectuera qu'une seule (un peu comme faire un seul rendu).


## Effect Creators :

Ils produisent dans le MW et executent directement des actions .

#### call : 

execute une fonction et retourne une promesse, met en pause la saga en attendant la réponse

#### put : 

est utilisé pour dispatcher une action.

#### Autres exemples : 

fork, select, race, spawn ,join, cancel,...