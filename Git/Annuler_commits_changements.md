
Il y a plusieurs méthodes pour revenir en arrière, annuler un changement:

`git checkout <nomDeMonCommit> ou <numeroDeMonCommit>` : Cette méthode permet de revenir à une ancienne version,
en gros sur la ligne du temps on dit "Je me repositionne à tel moment"

**IMPORTANT** Quand je fais un `git checkout` je retourne en arrière mais en dehors de HEAD (HEAD étant le instant actuel), 
il faut donc vraiment penser à faire une nouvelle branche puis à merge celle ci sur la branche actuelle sinon tout les changements resteront "a part".

`git revert <numeroDuCommit>` Cette commande permet  d'annuler le commit selectionné. **IL FAUT PENSER A PUSH DERRIERE POUR VALIDER LES CHANGEMENTS!**

`git reset <nomDuCommit>` cette commande supprime le commit mais laisse les ressources en places. En gros je reset mon commit et ensuite pour effacer les ressources quil reste en local je fais un git checkout <nomDesRessources>

Si je fais un `git reset --hard a1e8fb5`, et qu'ensuite je fais un `git log` alors je verrais que les commits qu'il y avait après a1e8fb5 n'apparaissent plus nul part. Cette commande est idéal pour les changements locaux. 
L'inconvénient c'est que si on a un dépot distant  sur lequel les commits précédents étaient push au moment de push (après ce reset) git va nous générer un problème , il faut donc dans ce cas préferer un git revert.

