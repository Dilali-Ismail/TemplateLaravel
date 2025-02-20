# Installation et exécution du projet Laravel avec Docker

Ce guide explique comment initialiser et configurer un projet Laravel 8 à l'intérieur d'un conteneur Docker.

## Exécution des commandes

### 1. Accéder au conteneur Laravel
```sh
docker exec -it laravel_app bash
```
Cette commande permet d'accéder au terminal interactif du conteneur Docker nommé `laravel_app`.

### 2. Créer un projet Laravel
```sh
composer create-project --prefer-dist laravel/laravel . "8.*"
```
Cette commande installe Laravel 8 dans le répertoire courant en utilisant Composer.

### 3. Attribuer les permissions nécessaires
```sh
chown -R www-data:www-data /var/www/html/storage
```
Cette commande change le propriétaire du dossier `storage` en `www-data` (utilisateur utilisé par le serveur web dans le conteneur).

```sh
chmod -R 775 /var/www/html/storage /var/www/html/bootstrap/cache
```
Cette commande accorde les permissions nécessaires pour que le serveur web puisse écrire dans les dossiers `storage` et `bootstrap/cache`.

### 4. Lancer le serveur Laravel
```sh
php artisan serve
```
Cette commande démarre le serveur de développement Laravel, accessible via `http://localhost:8000` par défaut.

## Remarque
- Assurez-vous que Docker et Composer sont correctement installés sur votre machine.
- Si vous utilisez un autre serveur (comme Nginx ou Apache), adaptez les permissions et configurations en conséquence.

Bonne utilisation de Laravel avec Docker ! 🚀