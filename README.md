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
  
  func("Test 1"); // logs: You passed a string.
  func(["Test 2", "P2 Test 2"]); // logs: You passed an array.
  func({ value: "test" }); // logs: You did not pass a string or an array.
```
