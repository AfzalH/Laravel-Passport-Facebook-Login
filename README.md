# Laravel Passport Facebook Login
Provides a new Laravel Passport Grant Client named `facebook_login`, allowing you to log a user in with just their Facebook Login token.

A new user will be created (and optionally assigned to an EnTrust role) if the email address doesn't exist.

## Installation:
Install with composer  `composer require danjdewhurst/laravel-passport-facebook-login`

### Versions:
* Laravel 5.4 and Passport 2.0 only supported at this time

## Setup:
* Add `Danjdewhurst\PassportFacebookLogin\FacebookLoginGrantProvider::class` to your list of providers **after** `Laravel\Passport\PassportServiceProvider`.
* Add `Danjdewhurst\PassportFacebookLogin\FacebookLoginTrait` Trait to your `User` model (or whatever model you have configured to work with Passport).
* Run `php artisan vendor:publish`, this will create a `config/facebook.php` file. More options will be added here in the future.
* Enter your Facebook App details in your `.env` file: `FACEBOOK_APP_ID` and `FACEBOOK_APP_SECRET`.

## How To Use:

* Make a **POST** request to `https://your-site.com/oauth/token`, just like you would a **Password** or **Refresh** grant.
* The POST body should contain `grant_type` = `facebook_login` and `fb_token` = `{token from facebook login}`.
* An `access_token` and `refresh_token` will be returned if successful.

## Assumptions:
* Your `User` model has the folowing fields:
* * `facebook_id`
* * `first_name`
* * `last_name`
* * `email`
* * `password`

## Credits:
* https://github.com/mirkco/Laravel-Passport-Facebook-Login
* https://github.com/mikemclin/passport-custom-request-grant
