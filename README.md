Yii2 Mimin
===============
Simple RBAC Manager fo Yii 2.0. Minify of yii2-admin extension

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist hscstudio/yii2-mimin "*"
```

or add

```
"hscstudio/yii2-mimin": "*"
```

to the require section of your `composer.json` file.


Configuration
-------------

Once the extension is installed, simply use it in your code by  :

in config
```php
'as access' => [
     'class' => 'hscstudio\mimin\components\AccessControl',
	 'allowActions' => [
		// add wildcard allowed action here!
		'site/login',
		'site/error',
		'debug/*',
		'mimin/*', // only in dev mode
	],
],
...,
'modules' => [
	'mimin' => [
		'class' => 'hscstudio\mimin\Module',
	],
	...
],
'components' => [
	'authManager' => [
		'class' => 'yii\rbac\DbManager', // only support DbManager
	],	
],
```

Because this extension use 'yii\rbac\DbManager'as authManager, so You should migrate rbac sql first:

```yii migrate --migrationPath=@yii/rbac/migrations```

and then migrate custom table for this extension

```yii migrate --migrationPath=@hscstudio/mimin/migrations```

Usage
-----

You can then access Auth manager through the following URL:

```
http://localhost/path/to/index.php?r=mimin/user
http://localhost/path/to/index.php?r=mimin/role
http://localhost/path/to/index.php?r=mimin/route
```
### User
For standard user management, create/update/delete user, and assign role to user

### Role
To define level access of user, what he superadmin?, staff?, cashier? etc. In this menu, You can assign permission / action route (actions in application, they are create, update, delete, etc) to role

### Route
To get all action route from application. In here, You can on / off permission so not shown in menu role, rename alias/type of action route, so easy readable by end user. 


www.HafidMukhlasin.com
Jakarta - Indonesia
