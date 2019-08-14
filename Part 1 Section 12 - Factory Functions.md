# Part 1 Section 12 - Factory Functions

## 12.1 - Design Patterns

 Patterns are commonly used ways of solving problems in a given programming language. The standard pattern is not necessarily the best way to solve the problem, but it can be tweaked to fit your needs.  

The patterns we'll cover here are **object creational patterns**, which include Factory Functions, Constructor Functions and Classes. These all help with the creation of objects. 

## 12.2 - What is an instance? 

Individual objects are created from recipes. A single individual object is an "instance", e.g. a bowl of soup. The recipe is what is used to create it, which can be either a factory or a constructor function for example. This defines the properties in the object. 

## 12.3 - Factory Functions 

A factory function is any function that returns an object literal that is not a constructor function or class. The object returned is an 'instance' of the factory function. 

For example: 

```javascript
function puppyFactory(name, breed) {
  return {
    name, //Defines the property "name", to be given the value passed in as name.
    breed
  }
}

const donut = puppyFactory('donut', 'bulldog');

console.log(donut);
```

creating the object is a bit more straight forward than using constructor syntax to create the dog instance, which requires the `new` keyword: 

```javascript
const donut = new MakePuppy('donut', 'bulldog')
```

If you want to add a custom prototype to the object, you'll need to use Object.create and won't be able to take advantage of the short syntax above:

```javascript
const twitterPrototype = {
	getHandle() {
	return `${this.handle}`
	}
}
const createTwitterUser = handle => {
	const newUser = Object.create(twitterPrototype);
	newUser.handle = `@${handle}`;
	newUser.followers = 0;
	return newUser;
}
```

