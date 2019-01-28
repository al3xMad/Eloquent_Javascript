
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