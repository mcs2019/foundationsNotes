## Part 1 Section 11 - The Prototype Chain

The prototype chain allows JS to search for properties on objects like strings, arrays, objects, etc. 

It will first look in the object itself, then the internal prototype `[[prototype]]`, which contains a reference to another object and searches in that object and its prototype and so on until null. 

The first place searched is the object itself, so for example if you do: 

```javascript
array.push = 4
array.push(5)
//Returns a not a function error
```

Push is going to be searched for in the array object, and found, so we won't go up a step in the prototype chain to find push in Array.prototype

You can access prototypes inside an object with `Object.getPrototypeOf()`

### 11.1 - Prototype Chain Advantages 

1. Methods only need to be defined once as opposed to being saved on thousands of instances. 
2. Easy to maintain files by changing code only in one place to correct a bug.

### 11.2 - Object.create()

To make objects that have an internal prototype, use `object.create()` and pass in the object you'd like to be the prototype. 

Example: 

```javascript
const cellPhoneUtilities = {
  turnOn() {
    return 'Phone is turned on';
  },
  createContact(name, number) {
    return `Name: ${name} and  Number: ${number} added to your contacts!`
  },
  connectToWifi() {
    return 'connected to wifi';
  }
};

const iPhone = Object.create(cellPhoneUtilities);
iPhone.type = 'iPhone';
console.log(Object.getPrototypeOf(iPhone));

const pixel = Object.create(cellPhoneUtilities);
pixel.type = 'Pixel';
console.log(Object.getPrototypeOf(pixel));

console.log(pixel.connectToWifi());
console.log(iPhone.turnOn());
```

### 11.3 - Methods and `this`

Suppose we want to add a "toggle power" function to our phone objects: 

```javascript
const iPhone = {
  type: 'iPhone',
  power: true,
  togglePower() {
    iPhone.power = !iPhone.power
  }
};

const pixel = {
  type: 'pixel',
  power: true,
  togglePower() {
    pixel.power = !pixel.power;
  }
};
```

We're repeating a lot of code here. To keep our code DRY (Don't Repeat Yourself) we want to refactor (replace code) the code to only have to define a toggle power function once, by referring to whatever object we need to (whether it's a pixel or an iPhone). We can put a function in the prototype of both cell phones (cell phone utilities) to do just this. A function that can be used to define multiple objects this way via the prototype is called a 'factory function'.

We use the 'this' keyword to stand in for the object which the function is attached to.

```javascript
const cellPhoneUtilities = {
  turnOn() {
    return 'Phone is turned on';
  },
  createContact(name, number) {
    return `Name: ${name} and  Number: ${number} added to your contacts!`
  },
  connectToWifi() {
    return 'connected to wifi';
  }
  togglePower() {
    this.power = !this.power
  }
};
```

#### 11.3.1 The Implicit Binding Rule 

Whenever a method is called on using the dot operator, the implicit binding rule states that any use of `this` in that method refers to the object to the left of the dot, e.g. :

```javascript
pizza.getSize()
```

Will make it so that any use of `this` inside the `getSize()` function refers to the `pizza` object. 

The place where the method is called is called the **call site**, and it defines `this`.

