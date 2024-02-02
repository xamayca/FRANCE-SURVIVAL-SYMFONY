# CREATION D'UN SITE WEB AVEC LE FRAMEWORK SYMFONY #

## CREATION DU DOSSIER ET DES PREMIERS ELEMENTS DE NOTRE SITE ##
- __Executer la commande :__ `symfony new FRANCE-SURVIVAL-SYMFONY`.
- __Lancé le serveur Local Symfony avec la commande :__ `symfony server:start`.
- __Verifier que le site fonctionne :__ `http://127.0.0.1:8000/`.

## UTILISER LA BARRE DE DEBUG DEV SYMFONY ##
- __Executer la commande :__ `composer req debug --dev`.
> Ajoute la barre de débogage Symfony pour faciliter le débogage des applications Symfony en mode développement.

## VERIFICATION DE LA SECURITE AVEC SYMFONY ##
- __Executer la commande :__ `symfony check:security`.
> - Utilisation de la commande pour vérifier la sécurité d'un projet Symfony.
> - Une bonne pratique de sécurité et d'exécuter cette commande régulièrement pour mettre à jour ou remplacer les dépendances compromises dès que possible.

## INSTALLATION DES BUNDLES REQUIS ##
- __Executer la commande :__ `composer require symfony/maker-bundle`.
> Cette commande installe le bundle "maker" de Symfony, nécessaire pour générer des contrôleurs et d'autres éléments essentiels de notre projet Symfony.".

## INSTALLATION DU BUNDLE TWIG ##
- __Executer la commande :__ `composer require twig`.
> Cette commande installe le bundle Twig, qui permet de gérer les templates et les vues dans un projet Symfony.".

## CREATION D'UN HOME CONTROLLER ET DE NOTRE PREMIERE PAGE ##
### LE HOME CONTROLLER SERS A L'AFFICHAGE DES VUES SIMPLE NE NECESSITANT PAS DE CONTROLLER UNIQUE A CETTE PAGE ###
#### C'EST A DIRE PAS DE LOGIQUE SUPPLEMENTAIRE ####
- __Executer la commande :__ `symfony console make:controller HomeController`.
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
- Importer la classe pour Response `use Symfony\Component\HttpFoundation\Response;`.
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

ICI APPARAIT LE CONTENU DE NOTRE PAGE HOME (templates/home/index.html.twig)

{% endblock %}
```
> - La balise `{% block title %}` contient le titre de notre page dans l'onglet du navigateur et doit être fermé par `{% endblock %}`.
> - La balise `{% block body %}` contient le contenu de notre page `templates/home/index.html.twig` affiché dans le navigateur et doit être fermé par `{% endblock %}`.

## VERIFICATION DE NOTRE CONTROLLER, NOTRE ROUTE ET NOTRE VUE #
- __Verifier que le site fonctionne en se rendant sur :__ `http://127.0.0.1:8000/`.
> Si tout va bien, on devrait voir apparaitre notre texte à l'écran, si c'est le cas, bravo voici notre premiere page personalisé Symfony !
> > ![img.png](readme-image/view-text-twig.png)

# INSTALLATION DE TAILWIND CSS #
## INSTALLATION DES BUNDLES REQUIS ##
- __Executer la commande :__ `composer require symfony/webpack-encore-bundle`.
> Ajoute le bundle "Webpack Encore" à un projet Symfony pour faciliter la gestion des ressources front-end (CSS, JavaScript, etc.).

- __Executer la commande :__ `npm install -D tailwindcss postcss postcss-loader autoprefixer`.
> installe des dépendances nécessaires pour utiliser le framework CSS "Tailwind CSS".

- __Executer la commande :__ `npx tailwindcss init -p`.
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
- __Executer la commande :__ `npm run watch` dans un nouveau terminal dédié.
> Surveille les fichiers de votre projet et compile automatiquement les modifications en temps réel.

## VERIFICATION DE NOTRE INSTALLATION DE TAILWIND CSS ##
- Se rendre dans `templates/home/index.html.twig` et ajouter les lignes :
```js
<h1 class="text-3xl font-bold underline text-red-500">
    ICI APPARAIT LE CONTENU DE NOTRE PAGE HOME (templates/home/index.html.twig)
</h1>
```
> Si tout va bien, on doit voir la police changée et notre `h1` être souligné en gras et Rouge !
> > ![img.png](readme-image/view-text-tailwind.png)


# AVANT DE COMMENCER ON PASSE A L'INSTALLATION DU BUNDLE DE SECURITE #
## DOIS OBLIGATOIREMENT ETRE INSTALLER AVANT LA CREATION DE L'ENREGISTREMENT, CONNEXION ETC.. (FORMULAIRES) ##
- __Executer la commande :__ `composer require symfony/security-bundle`.
> - Ce composant fait partie du système de sécurité de Symfony et offre des fonctionnalités pour gérer l'authentification, l'autorisation et la sécurité dans une application Symfony.
> - Cela inclut la configuration de l'authentification des utilisateurs, la gestion des rôles et des autorisations, ainsi que la protection contre les attaques CSRF (Cross-Site Request Forgery), etc.

## MISE EN PLACE D'UNE BARRE DE NAVIGATION DE BASE ##
- Se rendre sur `https://flowbite.com/docs/components/navbar/` et choisir une navbar simple.
- Se rendre dans `templates\base.html.twig` et y ajouter notre navbar au dessus de la balise `{% block body %}` pour que ce sois visible sur toutes nos pages.
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
- Se rendre sur le template twig `templates\home\test.html.twig` et y ajouter notre texte entre les balises `block` :
```js
{% block body %}

<h1 class="text-3xl font-bold underline text-blue-500">
    ICI APPARAIT LE CONTENU DE NOTRE PAGE TEST (templates/home/test.html.twig)
</h1>

{% endblock %}
```

### VERIFICATION DE NOTRE NOUVELLE ROUTE ET DE NOTRE NOUVELLE PAGE ###
- Se rendre sur `http://127.0.0.1:8000/`.
> Si tout va bien, quand on clique sur notre lien `test` dans la navbar, on doit être redirigé sur `http://127.0.0.1:8000/test` et voir notre `h1` apparaitre à l'écran.
> > ![img.png](readme-image/view-text-test-page.png)

# CREATION DE LA BASE DE DONNEE DE NOTRE PROJET SYMFONY #
## INSTALLATION DU BUNDLE DOCTRINE ##
- __Executer la commande :__ `composer require symfony/orm-pack`.
> - Cela va ajouter le bundle `doctrine/orm` ainsi que ses dépendances à votre projet Symfony.
> - Ce bundle permet d'intégrer Doctrine dans Symfony pour la gestion de la base de données et des entités (objet d'une table de base de données).

- __Executer la commande :__ `composer require symfony/maker-bundle --dev`.
> - Ajoute le symfony/maker-bundle comme dépendance de développement dans notre projet Symfony.
> - Cela signifie que le bundle sera utilisé uniquement pour le développement local et ne sera pas installé en production.
> - Le bundle Maker de Symfony fournit un ensemble de commandes pratiques qui aident à générer du code (comme des contrôleurs, des entités, des formulaires, etc.) et à accélérer le développement.

## CREATION DE NOTRE BASE DE DONEE ##
- Se rendre à la racine du projet Symfony dans le fichier `.env` et décommenter la ligne:
```js
DATABASE_URL="sqlite:///%kernel.project_dir%/var/data.db"
```
> Cette configuration utilise `SQLite` comme système de gestion de base de données.
- Puis toujours dans le `.env` décommenter la ligne :
```js
DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"
```
> - Cette configuration utilise `PostgreSQL` comme système de gestion de base de données, nous n'en voulons pas pour ce projet.
> - On peut ajuster la configuration pour utiliser d'autres systèmes de gestion de base de données, tels que `MySQL` ou `PostgreSQL`, en remplaçant l'URL de la base de données.
- __Executer la commande :__ `symfony console doctrine:database:create`.
> Cette commande crée la base de données pour notre projet Symfony en utilisant la configuration définie dans le fichier `.env`.

## LIAISON DE NOTRE BASE DE DONNEE A NOTRE PROJET SYMFONY ##
- Dans PHP Storm, cliquer sur l'icône base de donnée et ensuite :
> > ![img.png](readme-image/link-database-1.png)
> > ![img.png](readme-image/link-database-2.png)
> > ![img.png](readme-image/link-database-3.png)
> > ![img.png](readme-image/link-database-4.png)
> #### VERIFIER LES INFORMATIONS AVANT D'APPLIQUER ET DE VALIDER NOTRE LIAISON A LA BASE DE DONNEE.

### VERIFICATION DE LA CREATION DE NOTRE BASE DE DONNEE ###
- Se rendre à la racine de notre projet dans `var\data.db`.
> Ce fichier est pour l'instant vide, il se remplira quand on créera des entités avec Symfony.

## CREATION DE NOTRE PREMIERE ENTITY (TABLE) EN BASE DE DONEE ##
- __Executer la commande suivante dans un terminal :__ `symfony console make:user` et suivre les étapes :
```js
 The name of the security user class (e.g. User) [User]:
 > User

 Do you want to store user data in the database (via Doctrine)? (yes/no) [yes]:
 > yes

 Enter a property name that will be the unique "display" name for the user (e.g. email, username, uuid) [email]:
 > email

 Will this app need to hash/check user passwords? Choose No if passwords are not needed or will be checked/hashed by some other system (e.g. a single sign-on server).

 Does this app need to hash/check user passwords? (yes/no) [yes]:
 > yes

```
> - La premiere question demande le nom de l'entité, ce sera `User`.
> - La deuxième question demande si on veut la stocker avec doctrine dans notre base de données, `Yes` dans notre cas.
> - La troisième question demande de quelle façon nous voulons identifier nos utilisateurs de facon unique, ce sera `l'email` pour nous.
> - L'avertissement nous dit de choisir `No` si les mots de passe ne sont pas nécessaires ou s'ils seront vérifiés/hachés par un autre système.`
> - La quatrième question nous demande donc si on veut `hash(sécurité)` les mots de passe de nos utilisateurs, donc `Yes`.

# VERIFICATION DE LA CREATION DE NOTRE ENTITY USER #
- Le fichier `src\Entity\User.php`, dans Symfony représente la classe d'entité pour modéliser et gérer les utilisateurs d'une application web.
- Le fichier `src\Repository\UserRepository.php`, dans Symfony est généralement utilisé pour gérer les opérations de requête et d'accès à la base de données concernant les entités de l'utilisateur (User) de l'application..
> - __Executer la commande suivante dans un terminal :__ `symfony console d:s:u -f` pour mettre à jour le schéma de notre base de donnée.
> - Cliquer sur actualiser pour recharger la base de donnée dans notre IDE(PHP Storm).
> > ![img.png](readme-image/database-verification-user-creation-1.png)
> ![img.png](readme-image/database-verification-user-creation-2.png)

## AJOUTER UN CHAMP A NOTRE ENTITY USER (USERNAME) ##
- __Executer la commande :__ `symfony console make:entity` et suivre les étapes :
```js
Class name of the entity to create or update (e.g. VictoriousChef):
 > User

 Your entity already exists! So let's add some new fields!

 New property name (press <return> to stop adding fields):
 > username

 Field type (enter ? to see all types) [string]:
 > string

 Field length [255]:
 > 50 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no 

 updated: src/Entity/User.php
```
> - La premiere question demande le nom de l'entité que l'on veut créer où mettre à jour, nous allons mettre à jour `User`.
> - L'avertissement nous dit que notre entité existe déja, nous allons donc lui ajouter des champs.
> - La deuxième question demande quel nom attribuer à notre nouvelle propriété `username` dans notre cas.
> - La troisième question demande de quel type est la propriété que nous voulons ajouter `string (chaîne de caractères)` dans notre cas..
> - La quatrième question nous demande la longueur de notre string `50` caractères dans notre cas.
> - La cinquième question nous demande si notre propriété peu être null dans la base de donnéé, `No` dans notre cas.
> > Nous allons inviter l'utilisateur a entré son pseudo à l'inscription donc cette propriété est `obligatoire (Not null)`, on met `null` si on veut des `champs de formulaire facultatif` par exemple.
- __Executer la commande suivante dans un terminal :__ `symfony console d:s:u -f` pour mettre à jour notre table user.

### VERIFICATION DE L'AJOUT DU USERNAME A NOTRE TABLE USER ###
> - Se rendre dans l'interface de base de donnée de PHP Storm, actualiser, nous avons maintenant :
> ![img.png](readme-image/database-verification-username-creation-1.png)

> - **Command Terminal Utile:**`npm run install`.
> - **Command Terminal Utile:**`npm run watch`.
> - **Command Terminal Utile:**`composer install`.
> - **Command Terminal Utile:**`composer update`.