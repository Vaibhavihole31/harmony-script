## HarmonyScript: A Harmonious Journey through JavaScript's Best Practices

A mostly reasonable approach to JavaScript involves following best practices, writing clean and modular code, and utilizing appropriate design patterns. 🏆👉 

# Types

Understand the different types in JavaScript, including primitives and complex types.

## Primitives

Primitives are basic types in JavaScript. When you work with a primitive type, you directly manipulate its value. The following are the primitive types in JavaScript:

* `string` : Represents textual data.
* `number`: Represents numeric values.
* `boolean`: Represents true or false values.
* `null`: Represents the intentional absence of any object value.
* `undefined`: Represents an uninitialized or undefined value.
* `symbol`: Represents unique and immutable values that can be used as object keys.
* `bigint`: Represents arbitrary-precision integers larger than the range of the number type.

**Here are examples of each primitive type in JavaScript:**

```js
const str = 'Hello';        // string
const num = 42;             // number
const bool = true;          // boolean
const n = null;             // null
let und;                    // undefined
const sym = Symbol('foo');  // symbol
const bigInt = BigInt(123); // bigint

console.log(typeof str);    // Output: string
console.log(typeof num);    // Output: number
console.log(typeof bool);   // Output: boolean
console.log(typeof n);      // Output: object (typeof null is an implementation quirk)
console.log(typeof und);    // Output: undefined
console.log(typeof sym);    // Output: symbol
console.log(typeof bigInt); // Output: bigint
```

In this example, we define variables of each primitive type and use the `typeof` operator to determine their respective types. The `console.log` statements show the outputs when printing the types.

## Complex Types

Complex types refer to values that are composed of multiple components. When you work with complex types, you manipulate a reference to their value. The following are the complex types in JavaScript:

* `object`: Represents a collection of key-value pairs.
* `array`: Represents an ordered list of values.
* `function`: Represents reusable blocks of code.

**Here are examples of each complex type in JavaScript:**

```js
const obj = {                // object
  name: 'John',
  age: 30,
  city: 'New York'
};

const arr = [1, 2, 3];       // array

const func = function() {    // function
  console.log('Hello!');
};

console.log(typeof obj);     // Output: object
console.log(typeof arr);     // Output: object (arrays are a specialized type of object)
console.log(typeof func);    // Output: function
```

In this example, we define variables of each complex type. `obj` represents an object with properties for `name`, `age`, and `city`. `arr` represents an array with three elements. `func` represents a function that logs `Hello!` to the console.

The `typeof` operator is used to determine the types of `obj`, `arr`, and `func`. The `console.log` statements show the outputs when printing the types.ch

# Effective Variable Usage in JavaScript

## 1. Use `const` for all of your references

* When declaring variables that won't be reassigned, use const.

* Using `const` ensures that you can't accidentally reassign the reference, leading to more predictable and bug-free code.

* Examples:

```js
const a = 1;
const b = 2;
```

## 2. **Use `let` if you need to reassign references**

* If you need to reassign a reference, use `let` instead of `var`.

* `let` is block-scoped, meaning it is limited to the block where it's defined, unlike `var` which is function-scoped.

* Examples:

```js
let count = 1;
if (true) {
  count += 1;
}
```

## 3. **Block scope with `const`, `let`, and `var`**

* Both `const` and `let` are block-scoped, which means they only exist within the block they are defined in.

* `var`, on the other hand, is function-scoped.

* Examples:

```js
{
  let a = 1;
  const b = 1;
  var c = 1;
}
console.log(a); // ReferenceError
console.log(b); // ReferenceError
console.log(c); // Prints 1
```

In the above code, `a` and `b` will produce a `ReferenceError` because they are block-scoped, while `c` can be accessed because it is function-scoped.

# Object Creation

Use the literal syntax for object creation

Instead of using the **`new Object()`** syntax, it is recommended to use the curly braces **`{}`** to create objects.

**Bad Code :**

```js
const item = new Object();
```

**Good Code :**

```js
const item = {};
```

## Computed Property Names

Use computed property names when creating objects with dynamic property names
Computed property names allow you to define object properties dynamically using variables or function calls.


```js
function getKey(k) {
  return `a key named ${k}`;
}

// Bad
const obj = {
  id: 5,
  name: 'San Francisco',
};
obj[getKey('enabled')] = true;

// Good
const obj = {
  id: 5,
  name: 'San Francisco',
  [getKey('enabled')]: true,
};
```

In the bad example, the property name is assigned separately using square brackets. In the good example, the property name is computed directly within the object literal using square brackets.

## Object Method Shorthand

When defining methods in an object, you can use the shorthand syntax instead of the traditional function syntax.

**Bad Code :**

```js
const atom = {
  value: 1,

  addValue: function (value) {
    return atom.value + value;
  },
};
```

**Good Code :**

```js
const atom = {
  value: 1,

  addValue(value) {
    return atom.value + value;
  },
};
```
In the good example, the addValue method is defined using the shorthand syntax. It makes the code shorter and easier to read.

## Property Value Shorthand

When the property name and variable name are the same, you can use the property value shorthand syntax.

```js
const lukeSkywalker = 'Luke Skywalker';

// Bad
const obj = {
  lukeSkywalker: lukeSkywalker,
};

// Good
const obj = {
  lukeSkywalker,
};
```

In the bad example, the property name and variable name are repeated. In the good example, the property value shorthand is used to simplify the object literal.

## Grouped Shorthand Properties

When using shorthand properties, it is recommended to group them at the beginning of the object declaration. This makes it easier to identify which properties are using the shorthand syntax.

```js
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';

// Bad
const obj = {
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  lukeSkywalker,
  episodeThree: 3,
  mayTheFourth: 4,
  anakinSkywalker,
};

// Good
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  episodeThree: 3,
  mayTheFourth: 4,
};
```

In the bad example, the shorthand property **lukeSkywalker** is mixed with other properties. In the good example, all shorthand properties are grouped together, making them easier to locate.
