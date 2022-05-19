 On travaille tous pour Master/Main mais sans jamais coder dessus

 On mettra donc en place une branche dev qui sera mergée sur master à la toute fin du projet

 On tirera une nouvelle branche pour chaque fonctionnalité

 Une fois que cette branche sera terminée et si rien d'autre n'a été push sur dev depuis , on pourra directement se postionner sur dev et faire un `git merge <myBranch>`.
 Par contre il est probable comme on travail à plusieurs sur le projet que d'autres aient push avant moi sur dev. Pour être sur que je suis à jour, avant de faire mon merge, 
 il faut que je fasse un ``rebase``.  Depuis myBranch je fais un  'git rebase dev ' et ainsi je récupère le code à jour de dèv, même si celui  ci à avancé plus vite que moi. 
 Dès lors je peux  merger proprement ma branche  dessus !