# docker_php_mysql_template

## Prérequis
Avoir un client Docker installé et qui tourne.  
Démarer avec la commande 
```
docker compose up
```
Arrêter avec les touches [ctrl][c]

En cas de modification des paramètres du fichier docker-compose.yml ou des fichiers ini de PHP.
Soit :
```
docker compose up --build
```
ou si on à modifier que pour un service
```
docker compose up --build [nom du service : db, php-apache] 
```
Exemple:
```
docker compose up --build db 
```


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

Normalement, si depuis le menu Debug vous laisser VS le générer il faut juste ajouter le paramètre **Path Mapping** (ci-dessous) sous "port": 9003, dans la partie configuration.  
*Pensez à mettre une virgule après 9003*
```
            "pathMappings": {"/var/www/html": "${workspaceFolder}\\app"},
```
Mais comme launch.json est dans le dépot, tout devrait être Ok.
