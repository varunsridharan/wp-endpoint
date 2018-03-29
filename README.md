# VS WP Endpoint
Simple Lib To Handle Creation of Custom Endpoints Or Rewrites in WordPress 

## Usage
```php
$vs_wp_endpoint = new VS_WP_Endpoint('customprefix');
```

### Add End Point [ add_endpoint( $endpoint, $endpoint_type, $callback) ]
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
 ```
 #### PHP Code
 ```php
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
		echo 'Hi'
	}
}


```
---

### Add Rewrite Rules [ add_rewrite_rule( $path, $after ) ]
```php
/**
 * Adds Custom Rewrite Rules.
 *
 * @param string $path
 * @param string $after
 *
 * @return $this
 */
```

#### PHP Code
```php
// Below Will Be Converted into **http://example.com/mypath/22/xxx/
$vs_wp_endpoint->add_rewrite_rule('mypath/{user_id}/{user_name}','top');

// Below Will Be Converted into **http://example.com/welcome/EICAUTPPWICAASJEJNCA/
$vs_wp_endpoint->add_rewrite_rule('welcome/{verify_id}','top');
```
