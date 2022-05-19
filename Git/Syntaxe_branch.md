# Les types de branches:

Il faut distinguer trois types de branches :

## Les branches globales: 

On ne code jamais dessus, en fait elles servent pour le déploiement, on n'y met que du code qui proviendra de merge-requests après des codes reviews.

En général ces branches sont nommées: master, dev , ...

Dans un prochain document je definirai les principes de code-reviews et merge-requests.

## Les branches personnelles : 

 Il s'agit de branches sur lesquelles chaque dév codera de façon autonome. Ces branches sont destinées à être mergées (fusionnées) à la version de dev en cours.

 On les nommes comme suit : 

 `dev/[prenom]` ou `dev/[initiales]`

 ## Les branches de tâches:

Ces branches sont utiles quand un ou plusieurs dev vont travailler sur une branche qui n'est pas leur branche actuelle. Par exemple pour corriger un bug sur une version alors que le sprint actuel porte sur une autre version.

On se positionne donc sur la branche en question (celle que l'on doit fix) et on créera une branche spécifique pour cette tâche.
La syntaxe requise est la suivante : 

` fix/user-signup`
 `doc/missing-route`


## Les Syntaxes

Le schéma de base est le suivant  : 

`<type>/<name>/`

Comme pour les commits le **type** définit l'action majeure qui concerne la branche :

***feature***: Ajout d’une nouvelle fonctionnalité;

***bugfix***: Correction d’un bug;

***hotfix***: Correction d’un bug critique;

***chore***: Nettoyage du code;

***experiment***: Expérimentation de fonctionnalités.

Le **nom** lui va définir rapidement le but de la branche et DOIT être écrit en kebab-case


Pour résumer si je créer une branche pour réparer un bug qui concerne le formulaire d'inscription d'un utilisateur, je vais écrire

`dev/RP/bugfix user-form`

