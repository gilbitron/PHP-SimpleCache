The PHP SimpleCache Class is an easy way to cache 3rd party API calls. To use the class:

	require('simpleCache.php'); 
	$cache = new SimpleCache();
	$latest_tweet = $cache->get_data('tweet', 'http://search.twitter.com/search.atom?q=from:gilbitron&rpp=1');
	echo $latest_tweet;
	
A more advanced example:

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