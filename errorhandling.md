Errorhandling
=============
On failure the functions return an array with information on what went wrong. You can work with this array as much as you want to handle the errors.

Android
-------
```
array(2) {
  'errors' =>
  array(1) {
    'registrationID' =>
    string(15) "YOUR_ERROR_HERE"
  }
  'canonicalIDs' =>
  array(1) {
    'oldRegistrationID' =>
    string(4) "newRegistrationID"
  }
}
```

So in summary the array can contain two different arrays which represent the errors on the one hand and the canonicalIDs on the other hand, in both situations the registrationID on which the action occurred is the array key.

The following list of errors can occur:

* MissingRegistration → There was no registration id handed over
* InvalidRegistration → The sent registration id was corrupt
* MismatchSenderId → You are not allowed to send messages to this id (GCM settings)
* NotRegistered → The registration id isn't registered anymore and can be deleted from you database
* MessageTooBig → The payload is overflowing the maximum size of 4096 bytes
* InvalidDataKey → The payload contains a key which is registered by Google
* InvalidTtl → The value in the "time to live" field needs to be a value between 0 and 2,419,200 (4 weeks)

Canonical ids need to be changed in the database, otherwise they won't receive your next push message.

You can get more information in the [Android Developer Documentation - Error Codes](http://developer.android.com/google/gcm/gcm.html#error_codes)

iOS
---
```
array(2) {
  'errors' =>
  array(1) {
    '1234' =>
    string(15) "YOUR_ERROR_HERE"
  }
}
```

So in summary you get an array with the errors. Whereas the array keys represent the device tokens and the value is the error that occurred.

The following errors can occur:

* Processing error
* Missing device token
* Missing topic
* Missing payload
* Invalid token size
* Invalid topic size
* Invalid payload size
* Invalid token
* None (unknown)

More information on [Provider Communication with Apple Push Notification Service](http://developer.apple.com/library/mac/#documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CommunicatingWIthAPS/CommunicatingWIthAPS.html)
