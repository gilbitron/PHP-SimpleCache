The PHP SimpleCache Class is an easy way to cache 3rd party API calls. To use the class:

```php
require('simpleCache.php'); 
$cache = new SimpleCache();
$latest_tweet = $cache->get_data('tweet', 'http://search.twitter.com/search.atom?q=from:gilbitron&rpp=1');
echo $latest_tweet;
```
	
A more advanced example:

```php
require('simpleCache.php'); 
$cache = new SimpleCache();
$cache->cache_path = 'cache/';
$cache->cache_time = 3600;

if($data = $cache->get_cache('label')){
	$data = json_decode($data);
} else {
	$data = $cache->do_curl('http://some.api.com/file.json');
	$cache->set_cache('label', $data);
	$data = json_decode($data);
}

print_r($data);
```

PHP SimpleCache was created by [Gilbert Pellegrom](http://gilbert.pellegrom.me) from [Dev7studios](http://dev7studios.com)

Want to say thanks? [Consider tipping me](https://www.gittip.com/gilbitron).
