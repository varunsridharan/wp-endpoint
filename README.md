# WP Endpoint
Simple Lib To Handle Creation of Custom Endpoints Or Rewrites in WordPress 

[![Latest Stable Version](https://poser.pugx.org/varunsridharan/wp-endpoint/version)](https://packagist.org/packages/varunsridharan/wp-endpoint)
[![Total Downloads](https://poser.pugx.org/varunsridharan/wp-endpoint/downloads)](https://packagist.org/packages/varunsridharan/wp-endpoint)
[![Latest Unstable Version](https://poser.pugx.org/varunsridharan/wp-endpoint/v/unstable)](//packagist.org/packages/varunsridharan/wp-endpoint)
[![License](https://poser.pugx.org/varunsridharan/wp-endpoint/license)](https://packagist.org/packages/varunsridharan/wp-endpoint)
[![composer.lock available](https://poser.pugx.org/varunsridharan/wp-endpoint/composerlock)](https://packagist.org/packages/varunsridharan/wp-endpoint)


## Installation
The preferred way to install this extension is through [Composer](http://getcomposer.org/download/).

To install **WP_EndPoint library**, simply:

    $ composer require Varunsridharan/WP_Endpoint

The previous command will only install the necessary files, if you prefer to **download the entire source code** you can use:

    $ composer require Varunsridharan/WP_Endpoint --prefer-source

You can also **clone the complete repository** with Git:

    $ git clone https://github.com/varunsridharan/wp-endpoint.git

Or **install it manually**:

[Download WP_Endpoint.php](https://raw.githubusercontent.com/varunsridharan/wp-endpoint/master/class-endpoint.php):

    $ wget https://raw.githubusercontent.com/varunsridharan/wp-endpoint/master/class-endpoint.php


## Usage
```php
$vs_wp_endpoint = new \Varunsridharan\WordPress\Endpoint('customprefix');
```

### Add End Point [ `add_endpoint( $endpoint, $endpoint_type, $callback)` ]
```php
/**
 * Adds Custom Endpoints To Endpoints Array.
 *
 * @param string       $endpoint
 * @param int          $endpoint_type
 * @param array|string $callback 
 *                     if callback is a string and no function with the name then it will be triggered as action
 *
 * @example add_endpoint('hello/',EP_PAGES,'my_page_calback')
 * @example add_endpoint('world/',EP_PAGES,array(&$this,'page_callback'))
 *
 * @return $this
 */
 
 // With Action Trigger
 $vs_wp_endpoint->add_endpoint('myendpoint',EP_ROOT,'myendpoint_action');
 
 // With Function Callback
 $vs_wp_endpoint->add_endpoint('myendpoint2',EP_ROOT,'myendpoint_callback');
 
 // With Class Callback
 $vs_wp_endpoint->add_endpoint('myendpoint3',EP_ROOT,array('VS_CALLBACK_HANDLER','render'));


add_action('myendpoint_action','render_endpoint_page');

function render_endpoint_page($wp){
	var_dump($wp->query_vars);
}

function myendpoint_callback($wp){
	var_dump($wp->query_vars);
}

class VS_CALLBACK_HANDLER{
	public static function render($wp){
		echo 'Hi';
	}
}

```
---

### Add Rewrite Rules [ `add_rewrite_rule( $path, $after )` ]
```php
/**
 * Adds Custom Rewrite Rules.
 *
 * @param string $path
 * @param string $after
 *
 * @return $this
 */
 
// Below Will Be Converted into **http://example.com/mypath/22/xxx/
$vs_wp_endpoint->add_rewrite_rule('mypath/{user_id}/{user_name}','top');

// Below Will Be Converted into **http://example.com/welcome/EICAUTPPWICAASJEJNCA/
$vs_wp_endpoint->add_rewrite_rule('welcome/{verify_id}','top');
```

---

<!-- START common-footer.mustache  -->

<!-- END common-footer.mustache  -->
