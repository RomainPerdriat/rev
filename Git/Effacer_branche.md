`git branch -a`: Cette commande me permet d'afficher l'ensemble des branches; les locales ET les distantes

Si je veux supprimer une branche locale :

`git branch -d <maBranche>`: Cette commande est valable si tout les changements ont été commité et push
 Si ce n'est pas le cas il faudra faire un :
 `git branch -D <maBranche>`


 Si je veux supprimer une branche distante qui s'appelle 

  remote/origin/test

`git push origin --delete test`

si la branche s'appelle  

remote/devs/J

`git push devs --delet J`