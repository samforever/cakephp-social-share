CakePHP Social Share
====================

This plugin provides a CakePHP View helper for creating links to share content on numerous social networks and bookmarking sites.

The aim of the plugin is to keep things simple. It doesn't come packaged with any JavaScript and I leave design decisions up to you. You can choose whether you want to use text, images, sprites or an icon font for your links.

Social Share currently supports Delicious, Digg, Evernote, Facebook, Friend Feed, Google Bookmarks, Google+, LinkedIn, Newsvine, Pinterest, Pocket, Reddit Slashdot, simple email, StumbleUpon, Technorati, Tumblr and Twitter.

Installation
------------

Copy the plugin to your app/Plugin directory and rename the plugin's directory 'SocialShare'.

Then add the following line to your bootstrap.php to load the plugin.

    CakePlugin::load('SocialShare');

Usage
-----

### SocialShareHelper::link(string $service, string $title, mixed $url = null, array $options = array())

Returns an HTML link to share the current page for the supplied service. For example to create a link for Facebook:-

    echo $this->SocialShare->link(
    	'facebook',
    	__('Share on Facebook')
    );

You can easily produce a list of links to share to different social networks:-

    $services = array(
    	'facebook' => __('Share on Facebook'),
    	'gplus' => __('Share on Google+'),
    	'linkedin' => __('Share on LinkedIn'),
    	'twitter' => __('Share on Twitter')
    );

    echo '<ul>';
    foreach ($services as $service => $linkText) {
    	echo '<li>' . $this->SocialShare->link(
	    	$service,
	    	$linkText
	    ) . '</li>';
    }
    echo '</ul>';

Supported services:-

* delicious
* digg
* email
* evernote
* facebook
* friendfeed
* google (Google Bookmarks)
* gplus (Google+)
* linkedin
* newsvine
* pinterest
* pocket
* reddit
* slashdot
* stumbleupon
* technorati
* tumblr
* twitter

You can pass a URL or a routing array as the third parameter for the URL you want to share.

$options supports the same options as HtmlHelper::link() as well as a 'text' option for a page title you want to include when sharing the URL. For Pinterest there is an additional 'image' option for a URL to an image to share.

### SocialShareHelper::href(string $service, mixed $url = null, array $options = array())

Returns an URL for sharing to the supplied service.

### SocialShareHelper::fa(string $service, mixed $url = null, array $options = array())

Returns an HTML link just like SocialShare::link() except the link text will be a relevant Font Awesome icon for the service. For example:-

    echo $this->SocialShare->fa(
    	'facebook'
    	'http://example.com'
    );

Will output:-

    <a href="https://www.facebook.com/sharer/sharer.php?u=http%3A%2F%2Fexample.com"><i class="fa fa-facebook"></i></a>