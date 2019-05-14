## JavaScript Advanced Functions: The Collection-Processing Methods Family Tree

## Learning Goals

- Use `map` to transform an `Array`
- Use `reduce` to reduce an `Array` to a value
- Use JavaScript documentation to learn more about other variations on `map` and `reduce`
- Use `filter` to filter an `Array`

## Introduction

Now that you have written `map` and `reduce`, here's the big reveal: JavaScript
_already_ has these methods built into its `Array` data type!

## Use `map` to Transform an `Array`

```js
[10, 20, 30, 40].map(function(a) {
  return a * 2;
}); //=> [20, 40, 60, 80]
```

## Use `reduce` to Reduce an `Array` to a Value

```js
[10, 20, 30, 40].reduce(function(memo, i) { return memo + i }) //=> 100
[10, 20, 30, 40].reduce(function(memo, i) { return memo + i }, 100) //=> 200
```

Remember, **_JavaScript loves functions_.** By being able to pass functions
around comfortably, we can take advantage of methods that JavaScript gives us!
Given what you know about writing your own `map` and `reduce` functions,
read the JavaScript documentation and make sure you know how to use the
versions JavaScript provides you:

- [map][]
- [reduce][]

## Use JavaScript Documentation to Learn More About Other Variations on `map` and `reduce`

Now that we understand the "Character of Collection-Processing Methods" we are
ready to unleash the full power of this module! Instead of merely repeating
the documentation, we're going to help you apply your understanding to the
`filter` method, and then we're going to give you a list of document resources
you should look up and master.

## Filter

Look at the documentation for [filter][]. The syntax snippet is provided as:

```js
var newArray = arr.filter(callback(element[, index[, array]])[, thisArg])
```

> **NOTE**: This documentation uses `var` instead of `let`. In order to 
> honor that we're quoting another source, we've left the keyword `var`.
> You should prefer `let`, but it's good to recognize that sometimes
> documentation lags behind the current practice and you must do some 
> thoughtful interpretation on your own.

Here, we're told that on an `Array` (`arr`), we add a `.filter` and then,
between `()`, we provide a `callback` and a `thisArg`.

> **REMEMBER** Because of JavaScript's non-enforcement of _arity_, we
> don't **have to** provide all the arguments.

We'll talk a lot more about `this` and `thisArg` shortly, but for the moment,
we can _leave it out_.

Let's learn some more about the `callback`. The documentation tells us what
parameters it supports.

```js
// ... callback(element[, index[, array]]) ...)
```

Possible parameters:

1. `element`
2. `index` (optional)
3. `array` (optional)

JavaScript will move through the `Array` that `filter()` was invoked on and
pass the `element`, the `index` of that element, and the whole darn `array`
to the callback (called in the documentation, "`callback`").

Yet again, because of _arity_ non-enforcement, we don't *have* to add
parameters for `index` or `array`, or `element` even. Furthermore, in our
callbacks, we can name our parameters whatever we like. JavaScript always
makes those 3 arguments _available_ to our callback. What to call them and
whether to use them is entirely up to us. See examples below to see how we
can play with this.

Now, what happens in `callback`? The documentation tells us:

> Function is a predicate, to test each element of the array. Return true to
> keep the element, false otherwise. It accepts three arguments:

This function runs and has access to the parameters we just explained.

If the _call_ to `callback` returns `true`, that element will be added to an
invisible "keeper" `Array`; else, it's left out.

We can use the `element` or the `array` or the `index` or (more typically)
some interaction between them to create an expression that `return`s a
Boolean value from `callback`.

> **PRO-TIP**: After reading our description above, look at MDN's and make sure
> you know how to explain filter in your own words. Being able to learn from
> MDN is a core skill we must continually develop!

```js
[10, 20, 30, 40]
  .filter(function() {
    return true;
  }) //=> [10, 20, 30, 40] (map, basically)
  [(10, 20, 30, 40)].filter(function(e) {
    return e < 30;
  }) //=> [10, 20]
  [(10, 20, 30, 40)].filter(function(e, index) {
    return index % 2 === 0;
  }); // even-index elements
```

1. Map a collection
2. Only accumulate the elements that return a truthy value from the callback.
   The callback's mechanics are described above

Obviously, how we adjust the return value of the callback will decide whether
data we want is preserved or data we don't want is rejected.

## Provide a List of Collection-Processing Methods to Memorize

These are the collection-processing methods you should **_memorize_** and
practice heavily. They're going to be your friends every day in
JavaScript-land. There are other collection-processing methods that you might
not memorize, but it's pretty common for a developer to realize that they're
working in the "Character of collection-processing methods" and think, "Hm,
maybe there's a collection-processing method for that...." When that moment
hits, the developer comes _back_ to the documentation and look for that
"just-right" collection-processing method.

- [`every`][every]: Did all elements satisfy the callback?
- [`find`][find]: Find the first element that satisfies the callback
- [`findIndex`][findindex]: Find the first element that satisfies the callback's index
- [`map`][map]: Transform every element and create a new array
- [`reduce`][reduce]: Reduce every element into a new value
- [`some`][some]: Did any element satisfy the callback?

## Conclusion

Your programming power just increased by at least ten-fold. With these methods
and others provided in the documentation, you can tear through datasets
efficiently and flexibly. Enjoy the power!

[every]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every
[filter]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
[findindex]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex
[find]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find
[map]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
[reduce]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce
[some]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some
