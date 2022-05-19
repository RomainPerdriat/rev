les generateurs sont des fonctions normales si ce n'est que leur nom est précédé d'un *

`function* generator (){}`

`yield` est un mot clé utilisé de façon à découper en tâches qui se suivent (etape 1 mise en pause tant que étape 2 n'est pas terminée) l'execution de ma fonction. yield permet de faire un return sans pour autant mettre fin à ma fonction.

Les generators peuvent soit retourner une information soit la consommer.

Une function generator contient une méthode next().