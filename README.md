# Underbar
This project was written in the same spirit as [JavaScript Koans](https://github.com/mrdavidlaing/javascript-koans), and thusly
uses the [Mocha Test Suite](http://visionmedia.github.io/mocha/) to facilitate
a TDD approach to learning. It walks you through a reimplementation of
[underscore.js](http://underscore.js), a popular collection of useful functions
authored by Jeremy Ashkenas.

## What's in this repo?
* The file `src/underbar.js` is missing a few important functions and it's
  your job to fix the library by implementing them.
* The file `spec/underbarSpec.js` contains a test suite. Your goal is to get
  them all the tests to pass by implementing the missing functions.
* You can run the tests by opening `SpecRunner.html` in your browser.
* *Note: This repo using the Mocha testing suite as the means of checking your code.*
* **Some browsers support functions like `forEach`, `map`, `reduce` and `filter`.
  Don't use them to implement your own functions.**


## Notes

Some quick notes that might come in handy:

- Many of the functions operate on "collections." They can take both arrays or
  objects as their arguments and you need to be able to handle both cases. You
  can use `Array.isArray(obj)` to find out whether an object is an array, and
  you can use `obj.length` to test if something is either a string or an array.

- Within a function, you can use the `arguments` keyword to access all the
  parameters that were passed in, even if they aren't named in the function
  definition. This is useful if you don't know how many arguments are going to
  be passed in in advance. You can count the arguments by using `arguments.length`
  and access each argument using `arguments[i]`. It's very similar to an array,
  but note that it doesn't support most array functions (such as `slice` or
  `push`). You can read more about this
  [here](http://www.sitepoint.com/arguments-a-javascript-oddity/).

- If you have an array `myParameters` and would like to call a function
  `myFunction` using the elements in the array as parameters, you can use
  `myFunction.apply(context, myParameters)`. The first parameter, `context`, is
  the execution context for your function call. From inside `myFunction`, you
  can access it as `this`. For this exercise, you should be fine passing in the
  calling function's `this` for `context`. If you're curious, you can read more
  in the [documentation for apply](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Function/apply).

- Javascript has a built-in `Math` object that provides some useful functions.
  You can read up on them [here](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Math).

## Missing functions

The file `src/underbar.js` contains function definitions and
explanations for the following functions:

- [ ] last
- [ ] *first*
- [ ] each
- [ ] *indexOf*
- [ ] filter
- [ ] reject
- [ ] uniq
- [ ] map
- [ ] *pluck*
- [ ] invoke
- [ ] reduce
- [ ] *contains*
- [ ] every
- [ ] any
- [ ] extend
- [ ] defaults
- [ ] *once*
- [ ] memoize
- [ ] delay
- [ ] shuffle

***Extra Credit***

- [ ] sortBy
- [ ] zip
- [ ] flatten
- [ ] intersection
- [ ] difference
- [ ] chain
- [ ] throttle

Your goal for this exercise is to implement all of them and get all tests to
pass. *Italicized functions* are solved for you.

## Throttle Notes

There's one function that is a little more complicated, so we've included some
more context to help you along.

### `_.throttle(func, wait)`

Wrap a function `func` so that it can be called at most once within a period of
`wait` milliseconds. This is useful for throtteling access to expensive APIs or
drawing routines in a video game. Example:

```javascript
var counter = 0;
var inc = function() {
  return counter++;
};

// throttledInc gets called at most once every 100 ms
var throttledInc = _.throttle(inc, 100);

throttledInc(); // return 1, counter should now be 1
throttledInc(); // return 1, schedule inc() call in 100ms
throttledInc(); // return 1, should do nothing

// 100 ms later, inc is called

setTimeout(function(){
  throttledInc(); // return 2, schedule inc() call in 80ms
}, 120);

```

Arguments passed to the throttled function should be passed to the original
function.

The throttled function should always return the most recently returned value of
the original function.

If the wait period is 100ms and the function was last called 30ms ago, another
call to the throttled function should schedule a call for 0ms in the future.

# Looking for More?

If you've still got steam, download the real [underscore.js](https://github.com/documentcloud/underscore/) implementation and
test suite, and try to understand how it works. A great way to do this is to
break parts of the code and see which tests fail. For example, if you break
something in the `each` function, a large number of tests will suddenly fail.

Also try comparing your implementations to the ones in the real library.
