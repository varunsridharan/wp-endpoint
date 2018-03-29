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

class VS_CALLBACK_HANDLER{
	public static function render($wp){
		echo 'Hi'
	}
}


```
