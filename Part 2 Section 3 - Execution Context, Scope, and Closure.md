# Part 2 Section 3 - Execution Context, Scope, and Closure

## 3.1 - Scope 

Scope is basically what you have available to you in the area you are in a program. For instance in the example below: 

```javascript
let x = 2
if (isChecked) {
  let confirmed = true;
}
console.log(confirmed)
```

We will throw an error, because the scope of the variable `confirmed` is the if block. This particular kind of scope is called `block scope`, where the environment the variable is scoped to is a code block if it's declared with const or let. This was introduced in ES 2015. There's also Global scope for example, e.g. `x` above is globally scoped and accessible anywhere. 

You should never declare variables in global scope as it can get confusing and lead to collisions. 

## 3.2 - The Lexical Environment

Every scope has a lexical environment, which includes the things present in this scope (the variables available). Each lexical environment has: 

1. Environment Records
2. A link to its outer lexical environment.

There are two kinds of environment records in ES2015: 

1. Object Environment Record

2. Declarative Environment Record

   The important difference between these two is that the Object Environment Record stores values on the global object. This is the object references by `this` when you type it in the global scope. Variables created with var are stored here. Variables created with let or const are stored in the declarative record. 

   

   The link to the outer lexical environment is a component of the scope chain, the scope chain is kind of like the prototype chain in object definitions. 

   

   

