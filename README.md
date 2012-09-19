Code Igniter CAS Library
========================

This CodeIgniter library wraps around [phpCAS](https://wiki.jasig.org/display/CASC/phpCAS) (the official [CAS](http://en.wikipedia.org/wiki/Central_Authentication_Service) client from [Jasig](http://www.jasig.org)) to simplify use and configuration in a [CodeIgniter](http://www.codeigniter.com/) app.

To start using it, put your phpCAS installation in some accessible directory, copy `libraries/Cas.php` into your application's `libraries` folder and create a config file `config/cas.php` like this:

    <?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');
    $config['cas_server_url'] = 'https://yourserver.com/cas';
    $config['phpcas_path'] = '/path/to/phpCAS-1.3.1';
    $config['cas_disable_server_validation'] = TRUE;
    // $config['cas_debug'] = TRUE; // <--  use this to enable phpCAS debug mode

Having done that, in your controllers you should be able to do this:

    function index() {
        $this->load->library('cas');
        $this->cas->force_auth();
        $user = $this->cas->user();
        echo "Hello, $user->userlogin!";
    }


