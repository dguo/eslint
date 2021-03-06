# Disallow unncessary concatenation of strings (no-useless-concat)

It is unncessary to concatenate two strings together when they are on the same line since they could be combined into a single string ("a" + "b" -> "ab").

## Rule Details

This rule aims to flag the concenation of 2 literals when they could be combined into a single literal. Literals can be strings or template literals.

The following patterns are considered problems:

```js
/*eslint no-useless-concat: 2*/

// these are the same as "10"
var a = `some` + `string`; /*error Unexpected string concatenation of literals.*/
var a = '1' + '0';         /*error Unexpected string concatenation of literals.*/
var a = '1' + `0`;         /*error Unexpected string concatenation of literals.*/
var a = `1` + '0';         /*error Unexpected string concatenation of literals.*/
var a = `1` + `0`;         /*error Unexpected string concatenation of literals.*/
```

The following patterns are not considered problems:

```js
/*eslint no-useless-concat: 2*/

// when a non string is included
var c = a + b;
var c = '1' + a;
var a = 1 + '1';
var c = 1 - 2;
// when the string concatenation is multiline
var c = "foo" +
    "bar";
```

## When Not To Use It

If you don't want to be notified about unnecessary string concatenation, you can safely disable this rule.
