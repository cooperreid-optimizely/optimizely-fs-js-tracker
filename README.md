# Optimizely JSClient Manager
A solution for using Optimizely's Fullstack JavaScript SDK in the browser which handles SDK script & datafile fetching. The `optlyClientManager` provides wrapper functions for all of the Optimizely SDK's core methods.

---

## Enhancements

### init
Loads the SDK script and the datafile, returns a Promise
```javascript
optlyClientManager.init()
```

### user
Set the user's UUID and attributes. These values will automatically be used when calling all wrapper methods below.
```javascript
optlyClientManager.user('cp_reid', {'tier': 'gold'});
```

## Wrapper Methods

_Calling these methods will automatically attach the UUID and attributes set via `optlyClientManager.user`_

### track
(This can be called _prior_ to `init`)
```javascript
optlyClientManager.track('add_to_cart');
```

### activate & variation
Wrapper functions for Optimizely SDK methods `activate` and `getVariation`. The `activate` and `variation` method _must_ be called after `optlyClientManager` has initallized
```javascript
optlyClientManager.activate('exp_for_b');
optlyClientManager.variation('exp_for_b');
```

---

### Example:
```javascript
optlyClientManager.user('cp_reid', {'tier': 'gold', 'flag': 'B'});
optlyClientManager.track('add_to_cart');
optlyClientManager.init().then(function() {
  // activate and variation can be used here
});
```
