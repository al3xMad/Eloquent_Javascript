
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

## Values

To create a value, you must merely invoke its name.
Every value has to be stored somewhere, and if you want to use
a gigantic amount of them at the same time, you might run out of memory.
Fortunately, this is a problem only if you need them all simultaneously.

### Numbers

Values of the number type are, unsurprisingly, numeric values.

```javascript
13
```

Fractional numbers are written by using a dot.

```javascript
9.81
```

For very big or very small numbers, you may also use scientific notation by
adding an “e” (for “exponent”), followed by the exponent of the number:

```javascript
2.998e8
```

That is 2.998 × 10 8 = 299,800,000.
Calculations with whole numbers (also called integers) are guaranteed to always be precise.
Be aware of it and treat fractional digital numbers as
approximations, not as precise values.

## Arithmetic

The main thing to do with numbers is arithmetic. Arithmetic operations such
as addition or multiplication take two number values and produce a new number
from them.
The + and * symbols are called operators. The first stands for addition, and
the second stands for multiplication. For subtraction, there is the - operator, and division can be done with the /
operator.

```javascript
100 + 4 * 11
```

The multiplication happens first, but if you want addition to be first you only has to wrap the addition in parentheses.
When operators appear together without parentheses, the order in which
they are applied is determined by the precedence of the operators:  the / operator has the same
precedence as * . Likewise for + and - . When multiple operators with the same
precedence appear next to each other, as in 1 - 2 + 1 , they are applied left to
right. 

### Special numbers

There are three special values in JavaScript that are considered numbers but
don’t behave like normal numbers.
The first two are Infinity and -Infinity , which represent the positive and
negative infinities and the third one is NaN, which stands for “not a number”, even though it is a value of the number type (zero divided by zero)

###Strings

The next basic data type is the string. Strings are used to represent text. They
are written by enclosing their content in quotes.

```javascript
`Down on the sea`
"Lie on the ocean"
'Float on the ocean'
```

You can use single quotes, double quotes, or backticks to mark strings, as
long as the quotes at the start and the end of the string match.
Newlines (the characters
you get when you press Enter) may only be included when the string is quoted
with backtick ( \ ‘), the other types of strings have to stay on a single line.
To make it possible to include such characters in a string, the following
notation is used: whenever a backslash ( \ ) is found inside quoted text, it
indicates that the character after it has a special meaning. This is called
escaping the character.A quote that is preceded by a backslash will not end
the string but be part of it. When an n character occurs after a backslash, it is
interpreted as a newline. Similarly, a t after a backslash means a tab character.
Take the following string:

```javascript
"This is the first line\nAnd this is the second"
```

The actual text contained is this:

```javascript
This is the first line
And this is the second
```

If two backslashes follow each other,
they will collapse together, and only one will be left in the resulting string
value.
“A newline character is written like " \n " .” is:

```javascript
"A newline character is written like \"\\n\"."
```

Strings cannot be divided, multiplied, or subtracted, but the + operator can
be used on them. It does not add, but it concatenates

### Unary operators
Not all operators are symbols. Some are written as words. One example is the
typeof operator, which produces a string value naming the type of the value
you give it.

```javascript
console.log(typeof 4.5)
// → number
console.log(typeof "x")
// → string
```

We will use console.log in example code to indicate that we want to see the
result of evaluating something.
Operators that use two values are called binary operators, while those that
take one are called unary operators. The minus operator can be used both as
a binary operator and as a unary operator.

### Boolean values

It is often useful to have a value that distinguishes between only two possibili-
ties, like “yes” and “no” or “on” and “off”. For this purpose, JavaScript has a
Boolean type, which has just two values: true and false, which are written as
those words.

#### Comparison

Here is one way to produce Boolean values:

```javascript
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
```

The > and < signs are the traditional symbols for “is greater than” and “is
less than”, respectively. They are binary operators.
Strings can be compared in the same way.

```javascript
console.log("Aardvark" < "Zoroaster")
// → true
```

Other similar operators are >= (greater than or equal to), <= (less than or
equal to), == (equal to), and != (not equal to).
There is only one value in JavaScript that is not equal to itself, and that is
NaN (“not a number”).

#### Logical operators

JavaScript supports three logical operators: and, or, and not.
The && operator represents logical and. It is a binary operator, and its result
is true only if both the values given to it are true.

```javascript
console.log(true && false)
// → false
console.log(true && true)
// → true
```

The || operator denotes logical or. It produces true if either of the values
given to it is true.

```javascript
console.log(false || true)
// → true
console.log(false || false)
// → false
```

Not is written as an exclamation mark ( ! ). It is a unary operator that flips
the value given to it— !true produces false and !false gives true .
You can usually get by with knowing that of the operators we have seen so far, || has
the lowest precedence, then comes && , then the comparison operators ( > , == ,
and so on), and then the rest.
The last logical operator I will discuss is not unary, not binary, but ternary,
operating on three values. It is written with a question mark and a colon, like
this:

```javascript
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

The value on the left of
the question mark “picks” which of the other two values will come out. When
it is true, it chooses the middle value, and when it is false, the value on the
right.

#### Empty values

There are two special values, written null and undefined , that are used to
denote the absence of a meaningful value. They are themselves values, but
they carry no information.
The difference in meaning between undefined and null is an accident of
JavaScript’s design, and it doesn’t matter most of the time, so I recommend treating
them as mostly interchangeable.

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

### Summary

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