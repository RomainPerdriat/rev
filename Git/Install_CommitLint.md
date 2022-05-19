
On commence par faire un :
`npm install husky --save-dev`

Ensuite
`npx husky install`

Et
`npm set-script prepare "husky install"`

Enfin
`npm install @commitlint/cli @commitlint/config-conventional --save-dev`

Il faut maintenant créer un fichier `commitlint.config.js`
et dans celui-ci on fait : 
```js

    module.exports = {
  extends: ['@commitlint/config-conventional']
};

```

Ajouter : `npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'`

Ces manip installent des node_modules, il faut donc penser à les ajouter dans un .gitignore

Pour rappel la syntaxe à adopter et la suivante : 
`git commit -m "build : add config commitlint"`

Tester en premier lieu un message de commit faux pour s'assurer que c'est ok.