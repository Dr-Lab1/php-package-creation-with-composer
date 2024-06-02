# Comment créer un package PHP avec composer et le deployer

# Plan
- <a href="#installer-composer" > Installer Composer <a/>
- <a href="#créer-le-package" > Créer le package <a/>
- <a href="#tester-le-package-en-local" > Tester le package en local <a/>
- <a href="#tester-le-package-en-production" > Tester le package en production <a/>


# Installer composer

**Introduction**

Composer est un outil de gestion des dépendances en PHP. Il vous permet de déclarer les bibliothèques dont votre projet dépend et il les gérera (installation/mise à jour) pour vous.

**Gestion des dépendances**

Composer n'est pas un gestionnaire de packages dans le même sens que Yum ou Apt. Oui, il s'occupe de "packages" ou de bibliothèques, mais il les gère par projet, en les installant dans un répertoire (par exemple vendor) à l'intérieur de votre projet. Par défaut, il n'installe rien globalement. Il s'agit donc d'un gestionnaire de dépendances. Il supporte cependant un projet "global" par commodité via la commande global.

Cette idée n'est pas nouvelle et Composer est fortement inspiré par <a href="https://www.npmjs.com/" target="_blank">npm<a/> de node et <a href="https://bundler.io/" target="_blank">bundler<a/> de ruby.

<a href="https://getcomposer.org/doc/00-intro.md">La documentation officielle de Composer<a/>
 
<a href="https://getcomposer.org/download/">Le lien de téléchargement de Composer<a/> 

# Créer le package

**Initialisation du package**

Avant de commencer cette étape, il faut d'abord s'assurer que votre composer est installé et est à jour.


    composer init

Cette commande lancera une série de questions (prompts) qui permettront une configuration rapide et facile de notre package.
Certaines questions seront obligatoires (*) et d'autres seront optionnelles :

1. Package name (*)
   
   Ce paramètre est pris sous format \<vendor>/\<name>

   C'est un paramètre important parce qu'il servira de namespace aux futurs utilisateurs du package.
   Tâchez donc de bien entrer ces paramètres. Généralement, \<vendor> correspond au nom de l'entité qui a développé le package et \<name> le service du package

   ex: orange/orangemoney

   Attention :

   - No space
   - Lowercase format

2. Description

   C'est simplement décrire le package en quelque ligne. Ce paramètre est optionnel et peut être modifié à n'importe quel moment.

   ex: TaskManager est un gestionnaire de tâches...

4. Author

   C'est pour entrer le nom de l'auteur.
   Assez souvent, votre nom et votre email sont proposés par *Composer* lui-même. Dans ce cas, faites *enter* pour accepter, sinon entrez les informations que vous voulez bien

   Mais tout comme la description, l'auteur peut être modifié et on peut en rajouter autant qu'on veut.

   ex:
   
       [
    
         {
       
           "name": "Dr-Lab1",
           "email": "drlab1@gmail.com",
           "homepage": "https://github.com/Dr-Lab1",
           "role": "Head developer"
       
         },
       
         {
       
           "name": "Jonathan",
           "email": "jonathan@gmail.com",
           "homepage": "https://github.com/Dr-Lab1",
           "role": "developer"
       
         },
       
       ]

5. Minimum Stability

   Ce paramètre est l'indicateur de stabilité du package. Il est conseillé de le laisser vide car le package est dans sa création et on ne sait pas quantifier la sa stabilité

6. Package Type

   Le type de package à développer.
   
   ex:

   - library
   - project
   - metapackage
   - composer-plugin

7.  License

    C'est la license du package. Laissez un vide simplement si vous n'en avez pas.

Ces opérations vont résulter en un fichier ***composer.json*** qui renfermera les configurations remplies ci-heaut. Il y a plusieurs autres possibiltés telles que ajouter les *dependencies* avec require: {}

ex :


       {
           "name": "labyrinthe/payment",
           "autoload": {
               "psr-4": {
                   "Orange\\Orangemoney\\": "src/"
               }
           },
           "authors": [
               {
               
                   "name": "Dr-Lab1",
                   "email": "dblab1@gmail.com"
                   
               }
           ],
           "require": {}
       }

**Organisation du package**

Il y aura à la racine, un dossier ***src***, un dossier ***vendor***, et un fichier ***composer.json***.

Toute la logique du package sera codée dans le ***src***.


# Tester le package en local

1. Installer une nouvelle app laravel pour tester votre package. 

2. Allez sur composer.json de la nouvelle application et entrez ce code avant les propriétés ***require*** :

   
       "repositories":
       [
            {
       
                "type": "path",
                "url": "C:/laragon/www/orange-money"
       
            }
        ],

3. Faites cette commande composer


        composer require orange/orangemoney

# Tester le package en production

1. Créer votre compte <a href="https://packagist.org/" target="_blank">packagist<a/>

   Packagist est le dépôt principal de Composer. Il regroupe les paquets PHP publics installables avec Composer.
   Toutes les commandes **Composer** que nous faisons pour install ou update nos dépendances sont en fait dirigées vers packagist car c'est lui qui gère la plupart des dépendances PHP.

   De préférence, créer votre compte en utilisant votre compte GitHub possedant le code source de votre package.

2. Puis allez sur <a href="https://packagist.org/packages/submit">submit<a/>

   En allant sur submit, entrez le lien de votre repository GiHub abritant le code source de votre package.

   Assurez-vous qu'il soit **public** pour permettre à Packagist de l'enregistrer et d'y préléver certains détails importants, faire des mises à jour à chaque nouveau commit,... Remplissez les informations du package puis cliquer sur **submit**, voilà votre package est rendu public et utilisable partout dans le monde.

Maintenant essayons notre package dans notre application !

1. Installer une nouvelle app laravel pour tester votre package. 

3. Faites cette commande composer


        composer require orange/orangemoney

Vous pouvez maintenant faire tout ce que vous voulez.


Merci Infiniment d'avoir suivi ce tutoriel !
