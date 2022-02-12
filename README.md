laravel-whmcs

NOTE: This package is no longer in active development. Feel free to fork and extend it as needed.

A simple Laravel interface for interacting with the WHMCS API.

Installation

To install the package, simply add the following to your Laravel installation's composer.json file:

"require": {
	"laravel/framework": "5.*",
	"nicklaw5/laravel-whmcs": "dev-master"
},
Run composer update to pull in the files.

Then, add the following Service Provider to your providers array in your config/app.php file:

'providers' => array(
	...
	WHMCS\WHMCSServiceProvider::class
);
From the command-line run: php artisan vendor:publish

Configuration

Open config/whmcs.php and configure the api endpoint and credentials:

return [
	// API URL
	'url'		=>	'http://url.com/whmcs/includes/api.php',

	// API USERNAME
	'username'	=>	'admin_user',

	// API PASSWORD
	'password'	=>	'password123',

	// API RESPONSE TYPE
	'response_type'	=> 'json', // json or xml
];
Usage

// app/Http/routes.php

Route::get('/products/{client_id}', function() {

    $start = 0;
    $limit = 25;

    $products = WHMCS::getClientProducts($client_id, $start, $limit);

    return json_encode($products);
});
WHMCS Docs
