iOS Feedback Request
====================

To fetch the ran out device tokens from your iOS devices you need to call Apple's feedback server from time to time (~weekly).

With our 'bsc.iOSFeedback' service you can fetch all at once.

```php
$pem = "FULL_PATH_TO_PEM"
 
$oldTokens = $this->get('bsc.iOSFeedback')->getDeviceUUIDs($pem);
```

The following will get returned:

```
array(2) {
  [0] =>
  array(3) {
    'timestamp' =>
    int(1266604759)
    'length' =>
    int(32)
    'devtoken' =>
    string(32) "202cb962ac59075b964b07152d234b70"
  }
  [1] =>
  array(3) {
    'timestamp' =>
    int(1266604845)
    'length' =>
    int(32)
    'devtoken' =>
    string(32) "0ef5ec3e9f7781acca37c780b686cb61"
  }
}
```
