
# Javascript&#58; The Hidden Parts (Implicit and Automatic)

## Photo by Isis França on Unsplash

There is quite a lot of Javascript that you don’t have to type. From semicolons to implicit parameters. This article will show some examples of those either left out by design or corrected in an attempt to help the coder.

### Automatic Semicolon Insertion

It’s not just you! Other Javascript developers are lazy too. Despite ; being in the home row under your left pinky not everyone wants to type that every line end. So ECMA International decided during the process of making ES5 that they would remove that pressure. The rules were later expanded in ES2015 (ES6) and can be read [here](https://www.ecma-international.org/ecma-262/6.0/index.html#sec-automatic-semicolon-insertion) if desired.

For those who didn’t want to read the rules they break down to:

1. It will be inserted right before a line terminator (right before you hit return for a new line) of a valid segment of code

1. It will be inserted before } if needed

1. The beginning of the next line is not ( or one of the many other exemptions

Rule one exempts things like when you have a { right after a return, even on it’s own line. However if there is nothing there like ( or {. The practical effect of this is you could end up typing:

`return
 a+b`

and have semicolon added as

```
return;
a+b; 
```


There are more complicated exemptions, for example if/else statements won’t have a semi colon inserted after if’s {} when an else is there because that would violate how if/else works. There is such thing as valid grammar in ECMAscript and the automatic semicolon will not violate it.

[Bradley Braithwaite](http://www.bradoncode.com/blog/2015/08/26/javascript-semi-colon-insertion/) wrote a great piece on this that includes a fantastic diagram on the whole thing. I highly recommend reading through and heading his warnings about relying on automatic comma insertion.

### Implicit Coercion

As you may know there are no explicit types in JS. Your variable could at one moment be a string, and the next be a number if you so choose. I would suggest not choosing to do so as it would be confusing for most involved.

So what is implicit coercion? Pretty much this:

```
"2" + 1 = "21"
"2" - 1 = 1
1 + 1 + "2" = "12"
true + true = 2
3 + [1] = "31"
3 * [ 1 ] = 3
3 * [ 1, 2] = NaN
```


You may have seen something like this before, in some demon about Javascript quirks, or perhaps in your own work. There is a reason, it is that Javascript really wants to work. It wants to help you by ignoring the issues that occur when you would try to do an operation on two unlike types like string and number.

In Javascript the + operator is what is known as [overloaded](https://en.wikipedia.org/wiki/Operator_overloading) meaning that it does different things depending on what is around it. This particular overload is not unique to Javascript, and my attempt to figure out where it came from turned up nothing. If anyone knows, comment or send me a message and I’ll update with credit. So part of the confusing nature of this is understanding that if you use + that it is not considered a mathematical operator by default whereas things like -,*, and / are.

Back the topic at hand though. To show you what is happening here let me rewrite the above with what Javascript is actually doing:

```
"2" + String(1) = "21"
Number("2") - 1 = 1
String(1 + 1) + "2" = "22"
String(3) +[ 1 ].join() = "31" 
3 * Number([ 1 ].join()) = 3
3 * Number([ 1, 2 ].join()) = NaN //this comes from Number("1,2") which equals NaN
```


There is also another underlying logic here. Truthy/Falsy is a description of a Javascript value when it is forced to be converted to Boolean. Everything in Javascript is truthy besides:

* false

* 0

* null

* “”

* undefined

* NaN

* -0

You may have in fact already used that. For example if you check for something to be undefined you may write:

```
if(testVal){
  throw error
}
```


This is doing a == comparison of the value to `true` by converting the value `boolean(testVal)` because equality is a boolean operator. Earlier I had the example `true + true = 2` which is like writing `Number(true) + Number (true) = 2` . The plus converts them to numbers for the purposes of addition. To learn more of this madness check out this [chart ](https://dorey.github.io/JavaScript-Equality-Table/)which shows how all values can be compared with a ==.

### Implicit Return

In ES2015(ES6) the concept of arrow functions were introduced. Besides looking very cool (subjective) and reducing the amount of times you need to bind `this` especially in React, they also introduced the concept of implicit returns.

They are written like:

```
const testFunc = () => 'It worked!';
```


The =&gt; is also one of the cases implicit semicolon wouldn’t be applied. Once that string is added it would be. There is a few ways to break this:

```
const testFunc2 = () => {'It worked!'};

const testFunc3 = () => {return 'It worked!'};
```


What was added here were brackets ({}) which change the way the function is handled. As soon as they are added a return must be added or the return will be undefined. There are other gotchas here though:

```
const testFunc4 = () => {workingVal:'It worked!'};

const testFunc5 = () => ({workingVal:'It worked!'});
```


Make a guess which at which these will actually return an object and which will return undefined when called. The answer is testFunc5. The brackets get mistaken for the opening to a function body. The parentheses prevent that.

For implicit return to work the value after the arrow must be an expression. An expression in Javascript is something that produces a value when used. 1 + 1 is an expression that evaluates to 2. A statement is a bit different, for example `if/else` is a statement. There is no value after it has run without a return. Using an if will never allow implicit return to work. Ternary expressions however do work since their result is an expression.

Arrow functions have one other small piece of omission possible. If you have only one parameter you can leave out the parentheses. Having 0 or 2 plus means they are required. The exception to this being if you have default values set for your parameter.

### Implicit Function Params

When you create a function, even one without parameters defined there are still a few of them possible to call inside the function. The most obvious one is `this` which changes depending on how it’s being called. In a standard function called to return `this` it will return the global scope which is `window `in browser and `global` in Node. Call, apply, and bind can all change the scope that `this` refers to as can calling it as a method on an object.

Arrow methods also change the way `this` handled. The full scope of how `this` works is a bit outside the scope of this article however if you would like to learn more I’d suggest either the [MDN page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) or one of the large number of articles written by others.

While `this` is fairly common knowledge `arguments` is less so. In any function `arguments` is there, allowing you to call parameters in an array. This works even if there isn’t anything declared as a parameter. For example:

```
function arguementTest () {
  return arguments.length
}

arguementTest(0,1,2,3) // this will return 4
```


Given this is an array it is also possible to call arguments by number. In the example above if I had called `arguments[1]` I would have received a 1 in return a 1 as that is the second value. It should be noted that it is not truly an array. It can be accessed like one, and has a length property but`forEach()` or `pop()`will not work. Running `typeof` will show `arguments `to be an object. It will also not be possible to access the `arguments` in an arrow function.

MDN notes that you should not actually use this in ES2015(ES6)+ code. Instead you should prefer what is called a `rest parameter` . This is basically a spread operator added as the last parameter like so:

```
function restOp ( one, two, ...rest){
  return rest
}

restOp (0,1,2,3,4) // this will return [2,3,4]
```


It gives advantages like not having to account for your named parameters as well as actually being an array with all array methods intact. The rest parameter can be called what you like but must always be the last one specified.

### Outro

Hopefully this enlightened you to some of the things you can leave out of JS or that were there and you never realized. As always if I missed anything or got something wrong send me a message. If I discover something new or find that I’ve forgotten I will try to keep this article up to date.