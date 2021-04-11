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
## 📝 Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

[Checkout CHANGELOG.md](https://github.com/varunsridharan/wp-endpoint/blob/main/CHANGELOG.md)


## 🤝 Contributing
If you would like to help, please take a look at the list of [issues](https://github.com/varunsridharan/wp-endpoint/issues/).


## 📜  License & Conduct
- [**GNU General Public License v3.0**](https://github.com/varunsridharan/wp-endpoint/blob/main/LICENSE) © [Varun Sridharan](website)
- [Code of Conduct](https://github.com/varunsridharan/.github/blob/main/CODE_OF_CONDUCT.md)


## 📣 Feedback
- ⭐ This repository if this project helped you! :wink:
- Create An [🔧 Issue](https://github.com/varunsridharan/wp-endpoint/issues/) if you need help / found a bug


## 💰 Sponsor
[I][twitter] fell in love with open-source in 2013 and there has been no looking back since! You can read more about me [here][website].
If you, or your company, use any of my projects or like what I’m doing, kindly consider backing me. I'm in this for the long run.

- ☕ How about we get to know each other over coffee? Buy me a cup for just [**$9.99**][buymeacoffee]
- ☕️☕️ How about buying me just 2 cups of coffee each month? You can do that for as little as [**$9.99**][buymeacoffee]
- 🔰         We love bettering open-source projects. Support 1-hour of open-source maintenance for [**$24.99 one-time?**][paypal]
- 🚀         Love open-source tools? Me too! How about supporting one hour of open-source development for just [**$49.99 one-time ?**][paypal]

<!-- Personl Links -->
[paypal]: https://sva.onl/paypal
[buymeacoffee]: https://sva.onl/buymeacoffee
[twitter]: https://sva.onl/twitter/
[website]: https://sva.onl/website/


## Connect & Say 👋
- **Follow** me on [👨‍💻 Github][github] and stay updated on free and open-source software
- **Follow** me on [🐦 Twitter][twitter] to get updates on my latest open source projects
- **Message** me on [📠 Telegram][telegram]
- **Follow** my pet on [Instagram][sofythelabrador] for some _dog-tastic_ updates!

<!-- Personl Links -->
[sofythelabrador]: https://www.instagram.com/sofythelabrador/
[github]: https://sva.onl/github/
[twitter]: https://sva.onl/twitter/
[telegram]: https://sva.onl/telegram/


---

<p align="center">
<i>Built With ♥ By <a href="https://sva.onl/twitter"  target="_blank" rel="noopener noreferrer">Varun Sridharan</a> <a href="https://en.wikipedia.org/wiki/India">
   <img src="https://cdn.svarun.dev/flag-india.jpg" width="20px"/></a> </i> <br/><br/>
   <img src="https://cdn.svarun.dev/codeispoetry.png"/>
</p>

---


<!-- END common-footer.mustache  -->
