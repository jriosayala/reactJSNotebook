In this module, I provided a brief introduction into some core next-gen JavaScript features, of course focusing on the ones you'll see the most in this course. Here's a quick summary! 
### let & const
Read more about `let` : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let 
Read more about `const` : https://developer.mozilla.org/enUS/docs/Web/JavaScript/Reference/Statements/const 
`let` and `const` basically replace `var` . You use `let` instead of `var` and `const` instead of `var` if you plan on never re-assigning this "variable" (effectively turning it into a constant therefore). 
### ES6 Arrow Functions 
Read more: https://developer.mozilla.org/en-US/docs/Web/ JavaScript/Reference/Functions/Arrow_functions [[Arrow Functions Syntax|ArrowFunctions]] are a different way of creating functions in JavaScript. Besides a shorter syntax, they offer advantages when it comes to keeping the scope of the `this` keyword (see here). Arrow function syntax may look strange but it's actually simple.
```js
function callMe(name) {
	console.log(name);
}
``` 
which you could also write as:
```js
const callMe = function(name) {
	console.log(name);
}
``` 
becomes: 
```js
const callMe = (name) => {
	console.log(name);
} 
```
**Important:** When having no arguments, you have to use empty parentheses in the function declaration:
```js
const callMe = () => { console.log('Max!'); }
``` 
When having exactly one argument, you may omit the parentheses: 
```js
const callMe = name => { console.log(name); }
``` 
When just returning a value, you can use the following shortcut:
```js
const returnMe = name => name
``` 
That's equal to:
```js
const returnMe = name => { return name; }
```

### Classes 
Classes are a feature which basically replace constructor functions and prototypes. You can define blueprints for JavaScript objects with them.  
Like this: 
```js
class Person {
	constructor () {
		this.name = 'Max';
	}
}
const person = new Person();
console.log(person.name); 
// prints 'Max' In the above example, not only the class but also a property of that class (=> name ) is defined. 
```
They syntax you see there, is the "old" syntax for defining properties. In modern JavaScript projects (as the one used in this course), you can use the following, more convenient way of defining class properties:
```js
class Person {
	name = 'Max';
}
const person = new Person();
console.log(person.name); // prints 'Max' You can also define methods.
```
Either like this: 
```js
class Person {
	name = 'Max';
	printMyName () {
	console.log(this.name); // this is required to refer to the class! . 
}
const person = new Person();
person.printMyName();
```
Or like this: 
```js
class Person {
	name = 'Max';
	printMyName = () => { console.log(this.name); }
}
const person = new Person();
person.printMyName();
```
The second approach has the same advantage as all arrow functions have: The this keyword doesn't change its reference. You can also use inheritance when using classes: 

```js
class Human {
	species = 'human';
}
class Person extends Human {
	name = 'Max';
	printMyName = () => {
		console.log(this.name);
	}
}
const person = new Person();
person.printMyName();
console.log(person.species); // prints 'human' 
```

### Spread & Rest Operator 

^4ba648

The spread and rest operators actually use the same syntax:
```js
... 
``` 
Yes, that is the operator - just three dots. It's usage determines whether you're using it as the spread or rest operator. 
Using the Spread Operator: 
The spread operator allows you to pull elements out of an array (=> split the array into a list of its elements) or pull the properties out of an object. 

Here are two examples: 
```js
const oldArray = [1, 2, 3]; 
const newArray = [...oldArray, 4, 5];
// This now is [1, 2, 3, 4, 5]; 
```

Here's the spread operator used on an object:
```js
const oldObject = { name: 'Max' };
const newObject = { ...oldObject, age: 28 };
```

`newObject` would then be 
```js
{ name: 'Max', age: 28 } 
```
The spread operator is extremely useful for cloning arrays and objects. Since both are reference types (and not primitives), copying them safely (i.e. preventing future mutation of the copied original) can be tricky. With the spread operator you have an easy way of creating a (shallow!) clone of the object or array.  

**Destructuring**

Destructuring allows you to easily access the values of arrays or objects and assign them to variables. Here's an example for an array: 
```js
const array = [1, 2, 3];
const [a, b] = array;
console.log(a); // prints 1
console.log(b); // prints 2
console.log(array); // prints [1, 2, 3] 
```
And here for an object:
```js
const myObj = {
	name: 'Max', age: 28 
}
const {name} = myObj;
console.log(name); // prints 'Max'
console.log(age); // prints undefined
console.log(myObj); // prints {name: 'Max', age: 28}
```
Destructuring is very useful when working with function arguments. Consider this example:
```js
const printName = (personObj) => {
	console.log(personObj.name);
}
printName({name: 'Max', age: 28}); // prints 'Max'
```
Here, we only want to print the name in the function but we pass a complete person object to the function. Of course this is no issue but it forces us to call `personObj.name` inside of our function. We can condense this code with destructuring:
```js
const printName = ({name}) => {
	console.log(name);
}
printName({name: 'Max', age: 28}); // prints 'Max') 
```
We get the same result as above but we save some code. By [[Destructuring in Function Parameter Lists|destructuring]], we simply pull out the name property and store it in a variable/ argument named name which we then can use in the function body