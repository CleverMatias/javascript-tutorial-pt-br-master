# Type Conversions

Most of the time, operators and functions automatically convert a value to the right type. That's called "type conversion".

For example, `alert` automatically converts any value to a string to show it. Mathematical operations convert values to numbers.

There are also cases when we need to explicitly convert a value to put things right.

```smart header="Not talking about objects yet"
In this chapter we don't cover objects yet. Here we study primitives first. Later, after we learn objects, we'll see how object conversion works in the chapter <info:object-toprimitive>.
```

## ToString

String conversion happens when we need the string form of a value.

For example, `alert(value)` does it to show the value.

We can also use a call `String(value)` function for that:

```js run
let value = true;
alert(typeof value); // boolean

*!*
value = String(value); // now value is a string "true"
alert(typeof value); // string
*/!*
```

String conversion is mostly obvious. A `false` becomes `"false"`, `null` becomes `"null"` etc.

## ToNumber

Numeric conversion happens in mathematical functions and expressions automatically.

For example, when division `/` is applied to non-numbers:

```js run
alert( "6" / "2" ); // 3, strings are converted to numbers
```

We can use a `Number(value)` function to explicitly convert a `value`:

```js run
let str = "123";
alert(typeof str); // string

let num = Number(str); // becomes a number 123

alert(typeof num); // number
```

Explicit conversion is usually required when we read a value from a string-based source like a text form, but we expect a number to be entered.

If the string is not a valid number, the result of such conversion is `NaN`, for instance:

```js run
let age = Number("an arbitrary string instead of a number");

alert(age); // NaN, conversion failed
```

Numeric conversion rules:

| Value |  Becomes... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;and&nbsp;false</code> | `1` and `0` |
| `string` | Whitespaces from the start and the end are removed. Then, if the remaining string is empty, the result is `0`. Otherwise, the number is "read" from the string. An error gives `NaN`. |

Examples:

```js run
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (error reading a number at "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

Please note that `null` and `undefined` behave differently here: `null` becomes a zero, while `undefined` becomes `NaN`.

````smart header="Addition '+' concatenates strings"
Almost all mathematical operations convert values to numbers. With a notable exception of the addition `+`. If one of the added values is a string, then another one is also converted to a string.

Then it concatenates (joins) them:

```js run
alert( 1 + '2' ); // '12' (string to the right)
alert( '1' + 2 ); // '12' (string to the left)
```

That only happens when one of the arguments is a string. Otherwise, values are converted to numbers.
````

## ToBoolean

Boolean conversion is the simplest one.

It happens in logical operations (later we'll meet condition tests and other kinds of them), but also can be performed manually with the call of `Boolean(value)`.

The conversion rule:

- Values that are intuitively "empty", like `0`, an empty string, `null`, `undefined` and `NaN` become `false`.
- Other values become `true`.

For instance:

```js run
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```

````warn header="Please note: the string with zero `\"0\"` is `true`"
Some languages (namely PHP) treat `"0"` as `false`. But in JavaScript a non-empty string is always `true`.

```js run
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // spaces, also true (any non-empty string is true)
```
````


## Summary

There are three most widely used type conversions: to string, to number and to boolean.

**`ToString`** -- Occurs when we output something, can be performed with `String(value)`. The conversion to string is usually obvious for primitive values.

**`ToNumber`** -- Occurs in math operations, can be performed with `Number(value)`.

The conversion follows the rules:

| Value |  Becomes... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;/&nbsp;false</code> | `1 / 0` |
| `string` | The string is read "as is", whitespaces from both sides are ignored. An empty string becomes `0`. An error gives `NaN`. |

**`ToBoolean`** -- Occurs in logical operations, or can be performed with `Boolean(value)`.

Follows the rules:

| Value |  Becomes... |
|-------|-------------|
|`0`, `null`, `undefined`, `NaN`, `""` |`false`|
|any other value| `true` |


Most of these rules are easy to understand and memorize. The notable exceptions where people usually make mistakes are:

- `undefined` is `NaN` as a number, not `0`.
- `"0"` and space-only strings like `"   "` are true as a boolean.

Objects are not covered here, we'll return to them later in the chapter <info:object-toprimitive> that is devoted exclusively to objects, after we learn more basic things about JavaScript.
