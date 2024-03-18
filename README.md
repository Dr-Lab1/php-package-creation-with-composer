# Comment créer un package laravel avec composer et le deployer

# Plan
- <a href="#installer-composer" > Installer Composer <a/>

# Installer composer

**Introduction**

Composer est un outil de gestion des dépendances en PHP. Il vous permet de déclarer les bibliothèques dont votre projet dépend et il les gérera (installation/mise à jour) pour vous.

**Dependency management**

Composer n'est pas un gestionnaire de paquets dans le même sens que Yum ou Apt. Oui, il s'occupe de "paquets" ou de bibliothèques, mais il les gère par projet, en les installant dans un répertoire (par exemple vendor) à l'intérieur de votre projet. Par défaut, il n'installe rien globalement. Il s'agit donc d'un gestionnaire de dépendances. Il supporte cependant un projet "global" par commodité via la commande global.

Cette idée n'est pas nouvelle et Composer est fortement inspiré par npm de node et bundler de ruby.

https://getcomposer.org/doc/00-intro.md
<a href="https://getcomposer.org/download/">Le lien de téléchargement <a/> 

# Initialiser la creation du package
# Tester le package en local
# Tester le package en production

   
Install composer

composer init

[
  remplir les informations de la création
]


Installation du package en local
