# docker_php_mysql_template

## Prérequis
Avoir Visual Studio Code installé sur son ordinateur.

Avoir un client Docker installé et qui tourne.

Avoir quelques notions de l'utilisation des containers Docker.

Après avoir récupérer ce dépot sur son ordinateur et qu'il soit chargé dans VSC.

Démarer les containers avec la commande 
```
docker compose up
```
Arrêter avec les containers avec les touches [ctrl][c]

En cas de modification des paramètres du fichier docker-compose.yml ou des fichiers ini de PHP.
Soit pour recharger/reconstruire es services :
```
docker compose up --build
```
ou si on à modifier un fichier de paramétrisation et que l'on désire uniquement recharger/reconstruire un seul service
```
docker compose up --build [nom du service : db, php-apache] 
```
Exemple:
```
docker compose up --build db 
```

## Structure des dossiers du projet

A la raçine du projet vous trouverez le fichier ***docker-compose.yml*** qui contient la définition des containers Docker utilisé pour ce projet.

- **app** :  
  Contient les fichiers de l'application PHP 
  - index.php : Démarrage PHP
  - php_info.php : Informations de la configuration  
  - debug_info.php :  Information de la configuration de Xdebug


  Vous pouvez ajouter tous vos fichiers PHP nécéssaires à votre application dans ce dossier. 

  ***Par mesure de sécurité, éviter de déployer les fichiers php_info.php et debug_info.php sur votre serveur web de production.***

- **build**  
  - **php** : Contient le fichier Dockerfile pour l'image d'installation de PHP et des composants additionnels
- **php_config** :   
Contient les fichiers php.ini pour la config de PHP et xdebug.ini pour la config de Xdebug  

## Apache (Serveur web)
L'application est atteigable (après avoir démarrer les containers Docker) depuis http://localhost:8090

## Base de données MySQL
### Configuration
#### Sécurité
La sécurité pour l'accès à la base de données est configurée dans le fichier docker-compose, pensez à le modifier avec vos valeurs.

### Visualisation
Un client ***Adminer*** est disponible et atteiganble depuis http://localhost:8070
Pour la connexion 
- System = MySQL
- Server = db
- Username = root
- Password = dbo_test_pwd *"ou le password que vous avez mis pour le user root"*
- Database = *"Laiser vide"* 

Avec un autre client (comme MySQL Workbench)
- Connection Method = Standard (TCP/IP)
- Hostname = localhost
- Port = 3308
- Username = root
- Password = dbo_test_pwd *"ou le password que vous avez mis pour le user root"*
- Default Schema = *"Laiser vide"* 

## Configuration Xdebug
Ajouter l'extention PHP Debug" de Xdebug.org
Lire la documentation de l'extention afin de configurer le fichier launch.json.

Normalement, si depuis le menu Debug vous laisser VS le générer il faut juste ajouter le paramètre **Path Mapping** (ci-dessous) sous ***"port": 9003,*** dans la partie configuration.  
*Pensez à mettre une virgule après 9003*
```
            "pathMappings": {"/var/www/html": "${workspaceFolder}\\app"},
```
Mais comme launch.json est dans le dépot, tout devrait être Ok.
