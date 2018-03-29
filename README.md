# VS WP Endpoint
Simple Lib To Handle Creation of Custom Endpoints Or Rewrites in WordPress 

## Usage
```php
$vs_wp_endpoint = new VS_WP_Endpoint('customprefix');
```

### Add End Point
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
 
 
 
 $vs_wp_endpoint->add_endpoint('myendpoint',EP_ROOT,'myendpoint_action');
```
