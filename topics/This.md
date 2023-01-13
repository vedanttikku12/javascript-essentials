# this


**this** is an important concept in Javascript. I will stick my neck out and say it constitutes the backbone of JS. 

It refers to the execution context of a function.

What determines **this** value:

1) If a function is called normally, whether in a global scope or inside another function, its *this* value is window

2) If a function that is being called is a function expression (const x = function() {}), but created using arrow functions, that it will take the *this* binding of its parent function

```
  function parent() {

    const callback = () => {
      console.log('context_inner', this);
    }

    function HOF(cb) {
      console.log('context_outer', this);
      cb();
    }

    HOF.call({ a: 1});
  }

  parent.call({ b: 1 });

  // result

  context_outer window
  context_inner { b: 1 }
```

3) If a function is called with an object, the *this* value is of that object.