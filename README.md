# Project Processing Steps

This project build on Laravel with [jet-stream](https://jetstream.laravel.com/) stater kit. 
Further we use [LiveWire](https://laravel-livewire.com) with Blade template as scaffolding to [jet-stream](https://jetstream.laravel.com/)

We use the following commands to set up project.

```
composer create-project laravel/laravel PrizeBondManagement

composer require laravel/jetstream

php artisan jetstream:install livewire --teams
```

Now we run the project with following commend
```
php artisan serve
```

Now we are going to create some route for executing Artisan commends in [Commends.php](routes%2FCommends.php)
and include in [web.php](routes%2Fweb.php)

# Moving Routes to Our Routes
## Moving Fortify Routes
As [jet-stream](https://jetstream.laravel.com/) uses Laravel Fortify, so we are going to move all routes 
from vendor Laravel Fortify  `vendor\laravel\fortify\routes\routes.php` to our app [routes](routes) folder. 

We are going to create file in [routes](routes) folder,  name [Fortify.php](routes%2FFortify.php)
and place all routes form `vendor\laravel\fortify\routes\routes.php` and include file in 
[web.php](routes%2Fweb.php). Now to cut route from `vendor\laravel\fortify\routes\routes.php` we are going to place following code 
in [FortifyServiceProvider.php](app%2FProviders%2FFortifyServiceProvider.php)

```
public function register(){
    Fortify::ignoreRoutes();
}
```


---

# Implement Admin Theme
Starting with Admin panel, First we are going to update layout and apply admin theme. As our project is going to support
multiple language, so we will create two layouts, one for RTL(Right to Left) and one for LTR(Left to Right) and load them 
based on selected language type.

## Folder structure for layout View
First we are going to create folder `Panel` under [layouts](resources%2Fviews%2Flayouts).
Inside, [Panel](resources%2Fviews%2Flayouts%2FPanel) we have three more folders
+ [LTR](resources%2Fviews%2Flayouts%2FPanel%2FLTR) for LTR layout
+ [RTL](resources%2Fviews%2Flayouts%2FPanel%2FRTL) for RTL layout
+ [UniversalPartials](resources%2Fviews%2Flayouts%2FPanel%2FUniversalPartials) This folder is to place sections, those are common for both layouts LTR and RTL.


---



After updating [composer.json](composer.json) file you must need to run following command to successfully autoload your file
```
composer dump-autoload
```



Doing following steps to update login view
* load layout with layout tag `<x-auth-layout>`
* update HTML template
* update html components in [components](resources%2Fviews%2Fcomponents) folder
