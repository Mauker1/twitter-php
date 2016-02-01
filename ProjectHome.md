Twitter for PHP is a very small and easy-to-use library for sending messages to Twitter and receiving status updates with OAuth support.

![http://phpfashion.com/media/twitter-64.gif](http://phpfashion.com/media/twitter-64.gif)


# Usage #

Sign in to the http://twitter.com and register an application from the http://dev.twitter.com/apps page. Remember
to never reveal your consumer secrets. Click on My Access Token link from the sidebar and retrieve your own access
token. Now you have consumer key, consumer secret, access token and access token secret.

Create object using application and request/access keys

```
	$twitter = new Twitter($consumerKey, $consumerSecret, $accessToken, $accessTokenSecret);
```

The send() method updates your status. The message must be encoded in UTF-8:

```
	$twitter->send('I am fine today.');
```

The load() method returns the 20 most recent status updates
posted in the last 24 hours by you:

```
	$channel = $twitter->load(Twitter::ME);
```

or posted by you and your friends:

```
	$channel = $twitter->load(Twitter::ME_AND_FRIENDS);
```

or most recent mentions for you:

```
	$channel = $twitter->load(Twitter::REPLIES);
```

Extracting the information from the channel is easy:

```
	foreach ($statuses as $status) {
		echo "message: ", $status->text;
		echo "posted at " , $status->created_at;
		echo "posted by " , $status->user->name;
	}
```

The authenticate() method tests if user credentials are valid:

```
	if (!$twitter->authenticate()) {
		die('Invalid name or password');
	}
```

The search() method provides searching in twitter statuses:

```
	$results = $twitter->search('#nette');
```

The returned result is a PHP array:

```
	foreach ($results as $result) {
		echo "message: ", $result->text;
		echo "posted at " , $result->created_at;
		echo "posted by " , $result->form_user;
	}
```

Latest info is at [phpFashion](http://phpfashion.com/twitter-for-php).

# Download #

https://github.com/dg/twitter-php/releases/latest