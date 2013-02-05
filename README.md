The Basecom Push Bundle
=======================

How to install the bundle
-------------------------
For installing with composer use the following code:
```json
"require": {
"basecom/push-bundle": "dev-master"
}
```

The following options are available in your config.yml:

```yaml
basecom_push:
    ios:
      sandbox: false
      passphrase: YOUR_PEM_PASSPHRASE(Optional)
    android:
      apikey: YOUR_GCM_APIKEY_HERE(Possible to hand to the service directly)
```

Execute a push
--------------
To execute a push you need to do the following:
###Android###
```php
$keys = array('SOME_API_TOKEN',
              'ANTOHER_API_TOKEN');
$data = array('data' => array(
                    'message' => 'Hello World!',
            )); 
 
$apiKey = "OPTIONALLY_PUT_YOUR_APIKEY";
if(true === $this->get('bsc.androidPush')->push($data, $keys, $apiKey))
{
    echo 'It worked!';
}
```

###iOS###
```php
$keys = array('SOME_API_TOKEN',
              'ANTOHER_API_TOKEN');
$data = array('aps' => array(
                    'alert' => 'Hello World!',
            ));
 
$pem = "FULL_PATH_TO_PEM"
 
if(true === $this->get('bsc.iOSPush')->push($data, $keys, $pem))
{
    echo 'It worked!';
 
}
```

Both functions return "true" in case of success.

Advanced
--------
* [Errorhandling](errorhandling.md)  
* [Feedback Request](feedback.md)
