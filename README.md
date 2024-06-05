# Locale
- <a href="#Comment-créer-un-package-PHP-avec-composer-et-le-deployer" > Français <a/>
- <a href="#How-to-create-a-PHP-package-with-composer-and-deploy-it" > English <a/>

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
   Assez souvent, votre nom et votre email sont proposés par *Composer* lui-même. Dans ce cas, faites *enter* pour accepter, sinon entrez les informations que vous voulez bien.

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



Bien cordialement,

### <a href="https://github.com/Dr-Lab1/">Dr-Lab1<a/>




# How to create a PHP package with composer and deploy it

# Plan
- <a href="#install-composer" > Install Composer <a/>
- <a href="#create-package" > Create package <a/>
- <a href="#local-package-testing" > Local package testing <a/>
- <a href="#production-package-testing" > Production package testing <a/>

   
# Install composer
 
**Introduction**

Composer is a tool for dependency management in PHP. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.

**Dependency management**

Composer is not a package manager in the same sense as Yum or Apt are. Yes, it deals with "packages" or libraries, but it manages them on a per-project basis, installing them in a directory (e.g. vendor) inside your project. By default, it does not install anything globally. Thus, it is a dependency manager. It does however support a "global" project for convenience via the global command.

This idea is not new and Composer is strongly inspired by node's <a href="https://www.npmjs.com/" target="_blank">npm<a/> and ruby's <a href="https://bundler.io/" target="_blank">bundler<a/>.

### - <a href="https://getcomposer.org/doc/00-intro.md">Official Composer documentation<a/>
 
### - <a href="https://getcomposer.org/download/">Composer download link<a/> 

# Create package

**Package initialization**

Before starting this step, you need to make sure that your composer is installed and up to date.

    composer init

This command will launch a series of questions (prompts) that will allow quick and easy configuration of our package.
Some questions are mandatory (*), while others are optional :

1. Package name (*)
   
   This parameter is taken in the format \<vendor>/\<name>.

   This is an important parameter because it will serve as the namespace for future users of the package. Make sure you enter these parameters correctly.
   Generally, <vendor> corresponds to the name of the entity that developed the package and <name> to the package service.

         ex: orange/orangemoney

   Warning :

   - No space
   - Lowercase format

3. Description

   This simply describes the package in a few lines. This parameter is optional and can be changed at any time.
   
   ex: TaskManager is a task manager...

5. Author

   This is where you enter the author's name.
   Quite often, your name and e-mail address are suggested by *Composer* itself. In this case, press *enter* to accept, otherwise enter whatever information you like.

   But just like the description, the author can be changed and as many more added as you like.
   
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

7. Minimum Stability

   This parameter is the package stability indicator. It is advisable to leave it empty, as the package is still being created and its stability cannot be quantified.

8. Package Type

   Type of package to develop.
   
   ex:

   - library
   - project
   - metapackage
   - composer-plugin

9.  License

    This is the package license. Just leave it blank if you don't have one.

These operations will result in a ***composer.json*** file, which will contain the configurations filled in above. There are several other possibilities, such as adding *dependencies* with require: {}

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

At the root, there will be a ***src*** folder, a ***vendor*** folder, and a ***composer.json*** file.

All package logic is coded in the ***src***.


# Local package testing

1. Install a new laravel app to test your package. 

2. Go to composer.json of the new application and enter this code before the ***require*** properties:

   
       "repositories":
       [
            {
       
                "type": "path",
                "url": "C:/laragon/www/orange-money"
       
            }
        ],

3. Make this Composer command

        composer require orange/orangemoney

# Production package testing

1. Create your <a href="https://packagist.org/" target="_blank">packagist<a/> account

   Packagist is Composer's main repository. It contains all the public PHP packages that can be installed with Composer.
   All the **Composer** commands we issue to install or update our dependencies are in fact directed to packagist, as it manages most PHP dependencies.
   De préférence, créer votre compte en utilisant votre compte GitHub possedant le code source de votre package.

3. Go to <a href="https://packagist.org/packages/submit">submit<a/>

   On submit, enter the link to your GiHub repository containing the source code for your package.

   Make sure it's **public** to enable Packagist to register it and take important details from it, update it with each new commit, etc. Fill in the package details, click on **submit** and your package will be made public and available for use worldwide. Maintenant essayons notre package dans notre application !

* Install a new laravel app to test your package. 

* Make this Composer command


        composer require orange/orangemoney

Now you can do whatever you want.





Thank you so much for following this tutorial!

Best regards,

### <a href="https://github.com/Dr-Lab1/">Dr-Lab1<a/>
