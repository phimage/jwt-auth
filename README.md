# jwt-auth

> JSON Web Token Authentication for Laravel

[![Build Status](http://img.shields.io/travis/tymondesigns/jwt-auth.svg?style=flat-square)](https://travis-ci.org/tymondesigns/jwt-auth)
[![Scrutinizer Code Quality](http://img.shields.io/scrutinizer/g/tymondesigns/jwt-auth.svg?style=flat-square)](https://scrutinizer-ci.com/g/tymondesigns/jwt-auth/?branch=master)

#### *Docs work in progress!*

## Installation

Install via composer - edit your `composer.json` to require the package.

```js
"require": {
    "tymon/jwt-auth": "0.*"
}
```

Then run `composer update` in your terminal to pull it in.

Once this has finished, you will need to add the service provider to the `providers` array in `app/config/app.php` as follows:

```php
'Tymon\JWTAuth\JWTAuthServiceProvider'
```

Next, also in the `app/config/app.php` file, under the `aliases` array, you may want to add the `JWTAuth` facade.

```php
'JWTAuth' => 'Tymon\JWTAuth\Facades\JWTAuth'
```

Finally, you will want to publish the config using the following command:

```bash
$ php artisan config:publish tymon/jwt-auth
```

##### **Don't forget to set a secret key in the config file!**

And you're done!

## Basic Usage

### Creating Tokens

There are a number of ways you can generate a token. The usual flow would be to pass some credentials and the package will try to authenticate the user and return a fully formed JSON Web Token.

```php
$token = JWTAuth::attempt($credentials);
```

##### Creating a token based on a User object

```php
$user = User::find(1);
$token = JWTAuth::fromUser($user);
```
