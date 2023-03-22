# Object Conversion

When any object is being used in any computation where it needs to be converted to a primitive, it calls toString or valueOf depending on the context of its usage

For example:
```
const obj = {
  name: 'Sharan',
  age: 28
}


console.log(10 + obj); // 10[object object]
console.log(10 - obj); //NaN
```

The results are not much surprising as how can we add or subtract objects from a number.(In case of '+', it considers string concatenation)

To override this behaviour,

```
obj.toString = function() {
  return 'Sharan'
}

obj.valueOf = function() {
  return 1;
}

```

Now, let's try outputting few things to see the behaviour,

```
console.log(Number(website)); // 1
console.log(String(website)); // Sharan
console.log(Boolean(website)); // true

console.log(10 + obj); 11
console.log(10 - obj); 9

```

To convert to a primitive value, we can define a static property as follows

```
const obj = {
  name: 'Sharan',
  age: 28,
  [Symbol.toPrimitive](hint: 'string' | 'number' | 'default') {
    switch(hint) {
      case 'string':
        return 'Hello World';
      case 'number':
        return 5;
      default:
        return 2;
    }
  }
}

```

Now, doing type coercions and calculations, we get

```
console.log(Number(website)); // 5
console.log(String(website)); // Hello World
console.log(Boolean(website)); // true

console.log(10 + obj); 12
console.log(10 - obj); 5

```

The only thing surprising here is the addition operation. Here, the usage is not clear because of multiple usages of "+" operator. It could be either of numerical addition or string concatenation, hence, the _hint_ is "default" and the return value is 2. 

A thing to remember is that Symbol.toPrimitive will have higher priority than toString and valueOf.