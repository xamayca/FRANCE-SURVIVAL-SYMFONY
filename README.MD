# CREATION DU SITE WEB ARK: FRANCE SURVIVAL AVEC LE FRAMEWORK SYMFONY #

## CREATION DU DOSSIER ET DES PREMIERS ELEMENTS DE NOTRE SITE #
- __Executé la commande :__ `symfony new FRANCE-SURVIVAL-SYMFONY`.
- __Lancé le serveur Local Symfony avec la commande :__ `symfony server:start`.
- __Verifier que le site fonctionne :__ `http://127.0.0.1:8000/`.

## VERIFICATION DE LA SECURITE AVEC SYMFONY #
- __Executé la commande :__ `symfony check:security`.
> Utilisation de la commande pour vérifier la sécurité d'un projet Symfony.
> Une bonne pratique de sécurité et d'exécuter cette commande régulièrement pour mettre à jour ou remplacer les dépendances compromises dès que possible.

## INSTALLATION DES BUNDLES REQUIS ##
- __Executé la commande :__ `composer require symfony/maker-bundle`.
> Cette commande installe le bundle "maker" de Symfony, nécessaire pour générer des contrôleurs et d'autres éléments essentiels de notre projet Symfony.".

## INSTALLATION DU BUNDLE TWIG ##
- __Executé la commande :__ `composer require twig`.
> Cette commande installe le bundle Twig, qui permet de gérer les templates et les vues dans un projet Symfony.".

## CREATION D'UN HOME CONTROLLER ET DE NOTRE PREMIERE PAGE #
- __Executé la commande :__ `symfony console make:controller HomeController`.
> Cette commande générera un fichier de contrôleur dans le répertoire "src/Controller".

- Aller dans `src\Controller\HomeController.php` et modifier la fonction suivante `index()` en :
```js
    public function index(): Response
{
    return $this->render('home/index.html.twig', [
        'controller_name' => 'HomeController',
]);
}
```
- Importé la classe pour Response `use Symfony\Component\HttpFoundation\Response;`.
> Cette instruction permet d'utiliser la classe Response de Symfony pour gérer les réponses HTTP dans un projet Symfony.

- Crée le template Twig en passant la souris sur `'home/index.html.twig'`.
> Cette étape consiste à créer le fichier de modèle Twig associé à la page d'accueil de notre projet Symfony.

- Redirigé sur la racine de notre projet Symfony en changeant la route :
```js
#[Route('/home', name: 'app_home')] en #[Route('/', name: 'app_home')] 
```
> Cette modification de la route ajuste l'URL pour atteindre la page d'accueil de votre projet Symfony, de "/home" à la racine du projet ("/").

# VERIFICATION DE NOTRE CONTROLLER, NOTRE ROUTE ET NOTRE VUE #
- Aller dans `templates/home/index.html.twig` et modifier la fonction suivante `index()` en :
```js
    public function index(): Response
{
    return $this->render('home/index.html.twig', [
        'controller_name' => 'HomeController',
]);
}
```




# INSTALLATION DE TAILWIND CSS #
## INSTALLATION DES BUNDLES REQUIS ##
- __Executé la commande :__ `composer require symfony/webpack-encore-bundle`.
> Ajoute le bundle "Webpack Encore" à un projet Symfony pour faciliter la gestion des ressources front-end (CSS, JavaScript, etc.).

- __Executé la commande :__ `npm install -D tailwindcss postcss postcss-loader autoprefixer`.
> installe des dépendances nécessaires pour utiliser le framework CSS "Tailwind CSS".

- __Executé la commande :__ `npm install -D tailwindcss postcss postcss-loader autoprefixer`.
> Initialise la configuration de Tailwind CSS dans un projet en créant un fichier de configuration tailwind.config.js. 
> Et un fichier de plugins ("postcss.config.js") pour personnaliser les paramètres du framework Tailwind CSS.

### ACTIVER LE CHARGEMENT DE POSTCSS ###
- Se rendre dans `webpack.config.js` et ajouter la ligne :
```js
Encore
  // ...
  .enablePostCssLoader()
;
```
> Cela permet d'appliquer des transformations et des optimisations au code CSS de manière automatisée grâce aux plugins configurés dans notre projet.

### CONFIGURATION DE TAILWIND CSS POUR DETECTER LES CLASSES CSS ###
- Se rendre dans `tailwind.config.js` et ajouter les lignes :
```js
content: [
    "./assets/**/*.js",
    "./templates/**/*.html.twig",
]
```
> Nécessaire pour que Tailwind CSS détecte et traite les classes CSS utilisées dans les fichiers JavaScript ".js" et HTML Twig ".html.twig" de notre projet

### ACTIVATION DES CLASSES CSS AVEC TAILWIND CSS ###
- Se rendre dans `assets/styles/app.css` et ajouter les lignes :
```js
@tailwind base;
@tailwind components;
@tailwind utilities;
```
> Directives essentielles pour permettre à Tailwind CSS de reconnaître et d'appliquer les classes CSS utilisées dans les fichiers .js et .html.twig de notre projet.

### COMPILER NOS FICHIERS DE STYLES EN TEMPS REEL ###
- __Executé la commande :__ `npm run watch` dans un nouveau terminal dédié.
> Surveille les fichiers de votre projet et compile automatiquement les modifications en temps réel.

## VERIFICATION DE NOTRE INSTALLATION DE TAILWIND CSS ##
- Se rendre dans `assets/styles/app.css` et ajouter les lignes :
```js
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
```


Commande: `npm run install`.

Commande: `composer install`.