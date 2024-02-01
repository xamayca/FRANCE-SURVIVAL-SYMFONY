# CREATION DU SITE WEB ARK: FRANCE SURVIVAL AVEC LE FRAMEWORK SYMFONY #

## CREATION DU DOSSIER ET DES PREMIERS ELEMENTS DE NOTRE SITE #
- __Executé la commande :__ `symfony new FRANCE-SURVIVAL-SYMFONY`.
- __Lancé le serveur Local Symfony :__ `symfony server:start`.
- __Verifier que le site fonctionne :__ `http://127.0.0.1:8000/`.

# INSTALLATION DE TAILWIND CSS #
## INSTALLATION DES BUNDLES NECESSAIRE ##
- __Executé la commande :__ `composer require symfony/webpack-encore-bundle`.
> Ajoute le bundle "Webpack Encore" à un projet Symfony pour faciliter la gestion des ressources front-end (CSS, JavaScript, etc.).

- __Executé la commande :__ `npm install -D tailwindcss postcss postcss-loader autoprefixer`.
> installe des dépendances nécessaires pour utiliser le framework CSS "Tailwind CSS".

- __Executé la commande :__ `npm install -D tailwindcss postcss postcss-loader autoprefixer`.
> Initialise la configuration de Tailwind CSS dans un projet en créant un fichier de configuration ("tailwind.config.js"). 
> Et un fichier de plugins ("postcss.config.js") pour personnaliser les paramètres du framework Tailwind CSS.

### INSTALLATION DES BUNDLES NECESSAIRE ###
- Se rendre dans `webpack.config.js` et ajouter la ligne:
```js
Encore
  // ...
  .enablePostCssLoader()
;
```


Commande: `npm run install`.
Commande: `composer install`.