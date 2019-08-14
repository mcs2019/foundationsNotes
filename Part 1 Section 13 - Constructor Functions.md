# Part 1 Section 13 - Constructor Functions

## 13.1 - Constructor Functions 

Constructor functions allow you to create instances using the `new` keyword: 

```javascript
function Person(name) {
  this.age = 0;
  this.name = name;
}

var instanceObj = new Person('Sam');

console.log(instanceObj);
```



## 13.2 - `new` Operator and `this` Keyword Binding Rule

The `new` operator actually invokes the constructor function, so parentheses are not necessary if there are no arguments i.e. you can type `new Potato`. 

By default, the new operator makes an empty object literal be implicitly returned, so if you don't include anything in your constructor, an empty object is returned. 

The `this` keyword is assigned to the object you are going to create with `new`, it doesn't have any properties until you set its properties in the constructor function. 

## 13.2 - Function Prototype 

All functions have a prototype `Function.prototype` object. 

The `Function.prototype` is **NOT** the internal [[prototype]] of the function attached to the prototype chain, it is a separate function which includes the constructor function for that function. Below is the constructor function attached to an example hello world function which just returns 'Hello World'.

```javascript
//helloWorld.prototype.constructor 
function helloWorld () {
	return 'Hello World'
}
```

