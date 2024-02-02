# CREATION DU SITE WEB ARK: FRANCE SURVIVAL AVEC LE FRAMEWORK SYMFONY #

## CREATION DU DOSSIER ET DES PREMIERS ELEMENTS DE NOTRE SITE ##
- __Executé la commande :__ `symfony new FRANCE-SURVIVAL-SYMFONY`.
- __Lancé le serveur Local Symfony avec la commande :__ `symfony server:start`.
- __Verifier que le site fonctionne :__ `http://127.0.0.1:8000/`.

## UTILISER LA BARRE DE DEBUG DEV SYMFONY ##
- __Executé la commande :__ `composer req debug --dev`.
> Ajoute la barre de débogage Symfony pour faciliter le débogage des applications Symfony en mode développement.

## VERIFICATION DE LA SECURITE AVEC SYMFONY ##
- __Executé la commande :__ `symfony check:security`.
> - Utilisation de la commande pour vérifier la sécurité d'un projet Symfony.
> - Une bonne pratique de sécurité et d'exécuter cette commande régulièrement pour mettre à jour ou remplacer les dépendances compromises dès que possible.

## INSTALLATION DES BUNDLES REQUIS ##
- __Executé la commande :__ `composer require symfony/maker-bundle`.
> Cette commande installe le bundle "maker" de Symfony, nécessaire pour générer des contrôleurs et d'autres éléments essentiels de notre projet Symfony.".

## INSTALLATION DU BUNDLE TWIG ##
- __Executé la commande :__ `composer require twig`.
> Cette commande installe le bundle Twig, qui permet de gérer les templates et les vues dans un projet Symfony.".

## CREATION D'UN HOME CONTROLLER ET DE NOTRE PREMIERE PAGE ##
### LE HOME CONTROLLER SERS A L'AFFICHAGE DES VUES SIMPLE NE NECESSITANT PAS DE CONTROLLER UNIQUE A CETTE PAGE ###
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

### LA PAGE /base.html.twig ###
- Dans le fichier `templates/base.html.twig`, ajoutez les lignes :
```js
<h1> Ce titre est généré par BASE.HTML.TWIG !</h1>
<h2>La page <code>/base.html.twig</code> est un modèle de base dans un projet Symfony.</h2>
<h3>Elle définit la structure commune à l'ensemble du site web, y compris les éléments tels que l'en-tête, le pied de page, les menus de navigation, et d'autres éléments récurrents.</h3>
<h4>L'importance de l'extension {<code>% extends 'base.html.twig' %</code>} réside dans le fait qu'elle permet à d'autres pages, comme <code>/home/index.html.twig</code>, d'étendre cette structure de base.</h4>
```

### LA PAGE /home/index.html.twig ###
- Dans le fichier `templates/home/index.html.twig`, ajoutez la ligne :
```js
{% extends 'base.html.twig' %}
```
> - Cette ligne indique que le contenu de "index.html.twig" sera intégré dans le modèle "base.html.twig".
> - Permettant ainsi d'utiliser la structure définie dans "base.html.twig" pour la page d'accueil.

- Toujours dans le fichier `templates/home/index.html.twig`, ajoutez les lignes :
```js
{% block title %}  {% endblock %}

{% block body %}

ICI APPARAIT LE CONTENU DE NOTRE PAGE INDEX

{% endblock %}
```
> - La balise `{% block title %}` contient le titre de notre page dans l'onglet du navigateur et doit être fermé par `{% endblock %}`.
> - La balise `{% block body %}` contient le contenu de notre page `templates/home/index.html.twig` affiché dans le navigateur et doit être fermé par `{% endblock %}`.

## VERIFICATION DE NOTRE CONTROLLER, NOTRE ROUTE ET NOTRE VUE #
- __Verifier que le site fonctionne en se rendant sur :__ `http://127.0.0.1:8000/`.
> Si tout va bien, on devrait voir apparaitre notre texte à l'écran, si c'est le cas, bravo voici notre premiere page personalisé Symfony !
> ![img.png](readme-image/view-text-twig.png)

# INSTALLATION DE TAILWIND CSS #
## INSTALLATION DES BUNDLES REQUIS ##
- __Executé la commande :__ `composer require symfony/webpack-encore-bundle`.
> Ajoute le bundle "Webpack Encore" à un projet Symfony pour faciliter la gestion des ressources front-end (CSS, JavaScript, etc.).

- __Executé la commande :__ `npm install -D tailwindcss postcss postcss-loader autoprefixer`.
> installe des dépendances nécessaires pour utiliser le framework CSS "Tailwind CSS".

- __Executé la commande :__ `npx tailwindcss init -p`.
> - Initialise la configuration de Tailwind CSS dans un projet en créant un fichier de configuration tailwind.config.js. 
> - Et un fichier de plugins ("postcss.config.js") pour personnaliser les paramètres du framework Tailwind CSS.

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
> Nécessaire pour que Tailwind CSS détecte et traite les classes CSS utilisées dans les fichiers JavaScript ".js" et HTML Twig ".html.twig" de notre projet.

### ACTIVATION DES CLASSES CSS AVEC TAILWIND CSS ###
- Se rendre dans `assets/styles/app.css` et ajouter les lignes :
```js
@tailwind base;
@tailwind components;
@tailwind utilities;
```
> Directives essentielles pour permettre à Tailwind CSS de reconnaître et d'appliquer les classes CSS utilisées dans les fichiers .js et .html.twig de notre projet.

### INCLUSION DES FICHIERS CSS & JAVASCRIPT ###
- Se rendre dans `templates/base.html.twig` et ajouter les lignes :
```js
<head>
{% block stylesheets %}
{{ encore_entry_link_tags('app') }}
{% endblock %}

{% block javascripts %}
{{ encore_entry_script_tags('app') }}
{% endblock %}
</head>
```
> Ces blocs permettent d'inclure automatiquement les ressources front-end nécessaires à notre app Symfony avec les fonctions Twig "encore_entry_link_tags" et "encore_entry_script_tags".

### COMPILER NOS FICHIERS DE STYLES EN TEMPS REEL ###
- __Executé la commande :__ `npm run watch` dans un nouveau terminal dédié.
> Surveille les fichiers de votre projet et compile automatiquement les modifications en temps réel.

## VERIFICATION DE NOTRE INSTALLATION DE TAILWIND CSS ##
- Se rendre dans `templates/home/index.html.twig` et ajouter les lignes :
```js
<h1 class="text-3xl font-bold underline text-red-500">
    ICI APPARAIT LE CONTENU DE NOTRE PAGE INDEX
</h1>
```
> Si tout va bien, on doit voir la police changée et notre h1 être souligné en gras et Rouge !
> ![img.png](readme-image/view-text-tailwind.png)


# AVANT DE COMMENCER ON PASSE A L'INSTALLATION DU BUNDLE DE SECURITE #
- __Executé la commande :__ `composer require symfony/security-bundle`.
> - Ce composant fait partie du système de sécurité de Symfony et offre des fonctionnalités pour gérer l'authentification, l'autorisation et la sécurité dans une application Symfony.
> - Cela inclut la configuration de l'authentification des utilisateurs, la gestion des rôles et des autorisations, ainsi que la protection contre les attaques CSRF (Cross-Site Request Forgery), etc.

## MISE EN PLACE D'UNE BARRE DE NAVIGATION DE BASE ##
- Se rendre sur `https://flowbite.com/docs/components/navbar/` et choisir une navbar simple.
- Se rendre dans `templates\base.html.twig` et y ajouter notre navbar.
- Se rendre dans `src\Controller\HomeController` et trouvez le nom de la route que l'on veut utiliser (exemple : app_home).
- Les `href` dans Symfony s'écrivent de la manière suivante :
```js
<a href="{{ path('app_home') }}">
```
## AJOUT D'UNE NOUVELLE ROUTE ET D'UNE NOUVELLE VUE ##
- Se rendre dans `src\Controller\HomeConstroller.php` et y ajouter notre route test :
```js
#[Route('/test', name: 'app_test')]
public function contact(): Response
{
    return $this->render('home/test.html.twig', [
        'controller_name' => 'HomeController',
]);
}
```
- Passé la souris sur `'home/test.html.twig` pour générer automatiquement le template twig (la vue).
- Se rendre sur notre navbar dans `templates\base.html.twig` et y ajouter notre nouveau lien `{{ path('app_test') }}`.
- Se rendre sur le template twig `` et y ajouter notre texte entre les balises `block` :
```js
{% block body %}

    JE SUIS SUR MA PAGE DE TEST

{% endblock %}
```

### VERIFICATION DE NOTRE NOUVELLE ROUTE ET DE NOTRE NOUVELLE PAGE ###
- Se rendre sur `'home/test.html.twig` .



Commande: `npm run install`.
Commande: `composer install`.