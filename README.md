Code Igniter CAS Library
========================

## Attention: No longer maintained! Please reach out if you're interested in maintaining this library

This CodeIgniter library wraps around [phpCAS][1] (the official [CAS](http://en.wikipedia.org/wiki/Central_Authentication_Service) client from [Jasig](http://www.jasig.org)) to simplify use and configuration in a [CodeIgniter](http://www.codeigniter.com/) app.

Installing manually
===================

1. Download [phpCAS][1] and put it in some accessible directory.

2. Copy `libraries/Cas.php` into your CodeIgniter application's `libraries` folder

3. Create a config file `config/cas.php` like this:

<span/>

    <?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');
    $config['cas_server_url'] = 'https://yourserver.com/cas';
    $config['phpcas_path'] = '/path/to/phpCAS-1.3.1';
    $config['cas_disable_server_validation'] = TRUE;
    // $config['cas_debug'] = TRUE; // <--  use this to enable phpCAS debug mode


That's it, now you can test in a controller, doing something like this:


    function index() {
        $this->load->library('cas');
        $this->cas->force_auth();
        $user = $this->cas->user();
        echo "Hello, $user->userlogin!";
    }

Installing using Sparks
=======================

If your project is using [Sparks](http://getsparks.org/) to manage dependencies, you can get the latest version of this library with these steps:


1. Download [phpCAS][1] and put it in some accessible directory.
2. Install the latest version of the library using Sparks:
    php tools/spark install cas-auth-library
3. Create a config file `config/cas.php` like the example given for the manual installation.

Having done that, you should be able test it with this code:

    public function index() {
        $this->load->spark('cas-auth-library/0.0.2'); // update this according to the version you installed
        $this->load->library('cas');
        $this->cas->force_auth();
        $user = $this->cas->user();
        echo "Welcome, $user->userlogin!";
    }


[1]: https://wiki.jasig.org/display/CASC/phpCAS
