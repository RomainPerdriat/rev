## MERGE:

Avant de Merge, je vérifie avoir tout push sur ma branch à merger!

Je me déplace sur la branche qui va recevoir le merge.

`git fetch` va mettre à jour les derniers commits distants sur ma branche.

Ensuite je fais un `git merge <branch cible>`

Enfin je pense à supprimer la branche que je viens de merger.

Exemple : si je veux merge dev sur master,  je viens me positionner sur master puis je fais `git merge dev`.

## Fast-forward : 

Si master n'a pas bougé et que dev est avancé, quand je vais faire mon merge il va d'office faire un Fast-forward.
Comme au dessu je vais faire un checkout sur master puis un`git merge dev`.

## Rebase

J'ai deux branches: master  et dev

Je travaille sur Dev . Je commit 3 fois. 

Entre temps, mes collègues ont mergés leur travail sur master.
 Je veux récupérer ce qu'ils ont fait sur master sur mon dev. 
 J'ai deux solutions: 
 
 Je merge master sur mon dev, ce qui au niveau de l'hisorique  laissera  trace de mes 3 commits, mais seul le dernier sera à jour de master. 

 Je rebase master sur dev, ce qui concervera l'historique de mes 3 commits en les réécrivant un par un pour ajouter le contenu de master. cette démarche, en conservant mes trois commits me demandera donc de gérer des conflits individuellement pour chacun de mes commits.

`git checkout dev`
`git rebase master`



