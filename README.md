
# Eloquent_Javascript

## Table of Contents
  1. [ Values, Types, and Operators ]( # values, types, and operators )



## Introduction

## 1. Values, Types, and Operators

> “Below the surface of the machine, the program moves. Without
effort, it expands and contracts. In great harmony, electrons scatter
and regroup. The forms on the monitor are but ripples on the water.
The essence stays invisibly below.”
—Master Yuan-Ma, The Book of Programming

### Special numbers

There are three special values in JavaScript that are considered numbers but
don’t behave like normal numbers.
The first two are Infinity and -Infinity , which represent the positive and
negative infinities and the third one is NaN, which stands for “not a number”, even though it is a value of the number type (zero divided by zero)

#### Comparison

The > and < signs are the traditional symbols for “is greater than” and “is
less than”, respectively.
Strings can be compared in the same way.

```javascript
console.log("Aardvark" < "Zoroaster")
// → true
```

### Automatic type conversion

When an operator is applied to the “wrong” type of value, JavaScript will
quietly convert that value to the type it needs, using a set of rules that often
aren’t what you want or expect. This is called type coercion.

```javascript
console.log(8 * null)
// → 0
console.log("5" - 1)
// → 4
console.log("5" + 1)
// → 51
console.log("five" * 2)
// → NaN
console.log(false == 0)
// → true
console.log(null == undefined);
// → true
console.log(null == 0);
// → false
```

When you do not want any automatic type conversions to happen,
there are two additional operators: === and !== . The first tests whether a value
is precisely equal to the other, and the second tests whether it is not precisely
equal. So "" === false is false as expected.
I recommend using the three-character comparison operators defensively to
prevent unexpected type conversions from tripping you up.

#### Short-circuiting of logical operators

The logical operators && and || handle values of different types in a peculiar
way. They will convert the value on their left side to Boolean type in order
to decide what to do, but depending on the operator and the result of that
conversion.

```javascript
console.log(null || "user")
// → user
console.log("Agnes" || "user")
// → Agnes
```

We can use this functionality as a way to fall back on a default value.
The && operator works similarly, but the other way around. When the value
to its left is something that converts to false, it returns that value, and otherwise
it returns the value on its right.
Another important property of these two operators is that the part to their
right is evaluated only when necessary. In the case of true || X , no matter
what X is—even if it’s a piece of program that does something terrible—the
result will be true, and X is never evaluated. The same goes for false && X ,
which is false and will ignore X . This is called short-circuit evaluation.

### Summary (from book)

We looked at four types of JavaScript values in this chapter: numbers, strings,
Booleans, and undefined values.
Such values are created by typing in their name ( true , null ) or value ( 13
, "abc" ). You can combine and transform values with operators. We saw
binary operators for arithmetic ( + , - , * , / , and % ), string concatenation ( + ),
comparison ( == , != , === , !== , < , > , <= , >= ), and logic ( && , || ), as well as several
unary operators ( - to negate a number, ! to negate logically, and typeof to
find a value’s type) and a ternary operator ( ?: ) to pick one of two values based
on a third value.

## 2. Program structure

####Bindings

The special word (keyword) let indicates that this sentence is going to define a binding.
The words var and const can also be used to create bindings, in a way similar to let.

```javascript
let one = 1, two = 2;
console.log(one + two);
// → 3
var name = "Ayda";
const greeting = "Hello "; (not going to ever change)
console.log(greeting + name);
// → Hello Ayda
```

####Binding names

A binding name may include dollar signs ( $ ) or underscores ( _ ), but no other punctuation or special characters.
The full list of keywords and reserved words is rather long:
```javascript
break case catch class const continue debugger default
delete do else enum export extends false finally for
function if implements import interface in instanceof let
new package private protected public return static super
switch this throw true try typeof var void while with yield
```


## 3. Functions

####Arrow functions

The arrow comes after the list of parameters, and is followed by the function’s
body. It expresses something like “this input (the parameters) produces this
result (the body)”.
When there is only one parameter name, the parentheses around the param-
eter list can be omitted. If the body is a single expression, rather than a block
in braces, that expression will be returned from the function. So these two
definitions of square do the same thing:
```javascript
const square1 = (x) => { return x * x; };
const square2 = x => x * x;
```
When an arrow function has no parameters at all, its parameter list is just
an empty set of parentheses.
```javascript
const horn = () => {
console.log("Toot");
};
```

####Optional Arguments

JavaScript is extremely broad-minded about the number of arguments you
pass to a function. If you pass too many, the extra ones are ignored. If you
pass too few, the missing parameters get assigned the value undefined .

####Closure

A function that closes over some local bindings is called a closure. This behavior not only frees you from having to worry 
about lifetimes of bindings but also makes it possible to use function
values in some creative ways.
With a slight change, we can turn the previous example into a way to create functions that multiply by an arbitrary amount.
```javascript
function multiplier(factor) {
return number => number * factor;
}
let twice = multiplier(2);
console.log(twice(5));
// → 10
```

####Recursion

Recursion allows some functions to be written in a different style.
```javascript
function power(base, exponent) {
    if (exponent == 0) {
        return 1;
    } else {
        return base * power(base, exponent - 1);
    }
}
console.log(power(2, 3));
// → 8
```
But this implementation has one problem: in typical JavaScript implementations, it’s about 3 times slower
 than the looping version. Running through a simple loop is generally cheaper than calling a function multiple times.

####Growing functions

We want to write a program that prints two numbers, the numbers of cows
and chickens on a farm, with the words Cows and Chickens after them, and
zeros padded before both numbers so that they are always three digits long.

007 Cows
011 Chickens

This asks for a function of two arguments. Let’s get coding.

```javascript
function printFarmInventory(cows, chickens) {
let cowString = String(cows);
while (cowString.length < 3) {
cowString = "0" + cowString;
}
console.log(`${cowString} Cows`);
let chickenString = String(chickens);
while (chickenString.length < 3) {
chickenString = "0" + chickenString;
}
console.log(`${chickenString} Chickens`);
}
printFarmInventory(7, 11);
```

But just as we are about to send the farmer the code
(along with a hefty invoice), she calls and tells us she’s also started keeping
pigs, and couldn’t we please extend the software to also print pigs?

```javascript
function printZeroPaddedWithLabel(number, label) {
let numberString = String(number);
while (numberString.length < 3) {
numberString = "0" + numberString;
}
console.log(`${numberString} ${label}`);
53}
function printFarmInventory(cows, chickens, pigs) {
printZeroPaddedWithLabel(cows, "Cows");
printZeroPaddedWithLabel(chickens, "Chickens");
printZeroPaddedWithLabel(pigs, "Pigs");
}
printFarmInventory(7, 11, 3);
```

It works! But that name, printZeroPaddedWithLabel , is a little awkward.
It conflates three things—printing, zero-padding, and adding a label—into a
single function.
Instead of lifting out the repeated part of our program wholesale, let’s try
to pick out a single concept.

```javascript
function zeroPad(number, width) {
let string = String(number);
while (string.length < width) {
string = "0" + string;
}
return string;
}
function printFarmInventory(cows, chickens, pigs) {
console.log(`${zeroPad(cows, 3)} Cows`);
console.log(`${zeroPad(chickens, 3)} Chickens`);
console.log(`${zeroPad(pigs, 3)} Pigs`);
}
printFarmInventory(7, 16, 3);
```

## 4. Data Structures: Objects and arrays

####Data sets

The first index of an array is zero, not one.

####Properties

The two typical ways to access properties in JavaScript are with a dot and
with square brackets.
Both value.x and value[x] access a property on value — but not necessarily the same property. 
The difference is in how x is interpreted.
When using a dot, the word after the dot is the literal name of the property.
When using square brackets, the expression between the brackets is evaluated
to get the property name. Whereas value.x fetches the property of value
named “x”, value[x] tries to evaluate the expression x and uses the result as
the property name.

####Methods

The push method adds values to the end of an array, and the pop method
does the opposite, removing the last value in the array and returning it. So the thing that 
was added last is removed first.
```javascript
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push(5);
console.log(sequence);
// → [1, 2, 3, 4, 5]
console.log(sequence.pop());
// → 5
console.log(sequence);
// → [1, 2, 3, 4]
```

####Further arrayology

The corresponding methods for adding and removing
things at the start of an array are called unshift and shift.

```javascript
let todoList = [];
function remember(task) {
todoList.push(task);
}
function getTask() {
return todoList.shift();
}
function rememberUrgently(task) {
todoList.unshift(task);
}
```

To search for a specific value, arrays provide an indexOf method. It goes
through the array from the start to the end, and returns the index at which
the requested value was found—or -1 if it wasn’t found. To search from the
end instead of the start, there’s a similar method called lastIndexOf .

```javascript
console.log([1, 2, 3, 2, 1].indexOf(2));
// → 1
console.log([1, 2, 3, 2, 1].lastIndexOf(2));
// → 3
```

Both indexOf and lastIndexOf take an optional second argument that indi-
cates where to start searching.
Another fundamental array method is slice , which takes start and end in-
dices and returns an array that has only the elements between them. The start
index is inclusive, the end index exclusive.

```javascript
console.log([0, 1, 2, 3, 4].slice(2, 4));
// → [2, 3]
console.log([0, 1, 2, 3, 4].slice(2));
// → [2, 3, 4]
```

When the end index is not given, slice will take all of the elements after the
start index. You can also omit the start index to copy the entire array.
The concat method can be used to glue arrays together to create a new array,
similar to what the + operator does for strings.

```javascript
function remove(array, index) {
return array.slice(0, index)
.concat(array.slice(index + 1));
}
console.log(remove(["a", "b", "c", "d", "e"], 2));
// → ["a", "b", "d", "e"]
```

####Strings and their properties
