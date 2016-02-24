# fn.js
JavaScript Function type check and overloading

AMD compatible. If AMD is not used then use 'window.fn'.

```javascript
  var func = fn(fn([String], function(val) {
    console.log("You passed a string.").
  }), fn([Array], function(arr) {
    console.log("You passed an array.")
  }), function(obj) {
    console.log("You did not pass a string or an array.");
  });
  
  func(""); // logs: You passed a string.
  func([]); // logs: You passed an array.
  func({}); // logs: You did not pass a string or an array.
```

Overloaded functions are evaluated in order. So be careful and put the most specific functions first:

```javascript

require(["fn"], function(def) {

  function _handlestring(str) {
    console.log("_handlestring called.");
  }
  
  function _handlestring_fn(str, fn) {
    console.log("_handlestring_fn called.");
  }
  
  var handler = def(def([String], _handlestring), def([String, Function], _handlestring_fn));
  
  handler("", def); // logs _handlestring called.
  
}
```

fn only checks the arguments that are defined such that any additional arguments can be considered 'any' type. This also means that, as in the example above, if you define a handler that will always match before a more specific handler then the more specific one will never be called. The above example should be changed as follows:

```javascript
var handler = def(def([String, Function], _handlestring_fn), def([String], _handlestring));
handler("", def); // logs _handlestring_fn called.
```
