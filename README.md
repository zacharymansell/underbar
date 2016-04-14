# Underbar

This project was written in the same spirit as
[JavaScript Koans](https://github.com/mrdavidlaing/javascript-koans), and thusly
uses the [Mocha Test Suite](http://visionmedia.github.io/mocha) to facilitate a
TDD approach to learning. It walks you through a reimplementation of
[underscore.js](http://underscorejs.org/), a popular collection of useful functions
authored by Jeremy Ashkenas.

#### If you are in Precourse, please skip the entire 'Install Pomander' section

## Install Pomander

In Terminal, run the following command from within this repository:
```
curl -s https://raw.githubusercontent.com/hackreactor-labs/pomander/master/bin/install | bash
```
[Pomander](https://github.com/hackreactor-labs/pomander) will check your code for syntax errors and violations against the [style guide](http://bookstrap.hackreactor.com/wiki/Style-Guide) before each commit.

It uses a pre-commit hook to run staged files through `eslint` before each commit. `eslint` is a linter that will block your commit should you have any syntax errors, or, should you violate the Hack Reactor style guide. There are some preferred whitespace style rules that will give warnings but not block your commit. Your work will be of a higher quality if you follow the instructions of the linter. That said, if the linter gives you any funny bugs, these bugs are not intentional, and you should feel free to skip using it during commits with the `--no-verify` option.

## Links and Resources

Some quick notes that may come in handy:

- As you work through these functions, you may sometimes have questions about
  what arguments they take, or about how they work (their *interface*). If the
  inline comments don't clarify these questions, it's a good idea to reference
  the official library's [documentation](http://underscore.js).
- Many of the functions operate on "collections." They can take both arrays or
  objects as their arguments and you need to be able to handle both cases.
    - You can use `Array.isArray(obj)` to find out whether an object is an array.
    - You can use `obj.length` to test if something is either a string or an
      array.
- Javascript has a built-in `Math` object that provides some very useful
  functions. You can read up on them [here](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Math).
- Within a function, you can use the `arguments` keyword to access all the
  parameters that were passed in--even if they aren't named in the function
  definition. This is useful if you don't know how many arguments are going to
  be passed in in advance.
    - You can count the arguments by using `arguments.length` and access each
      argument using `arguments[i]`.
    - The `arguments` object is very similar to an array, but note that it does
      not support most array functions (such as `slice` or `push`). You can read
      more about this [here](http://www.sitepoint.com/arguments-a-javascript-oddity/).
- If you have an array `myParameters` and would like to call a function
  `myFunction` using the elements in the array as parameters, you can use
  `myFunction.apply(context, myParameters)`. The first parameter, `context`, is
  the execution context for your function call. From inside `myFunction`, you
  can access it as `this`. For this exercise, you can just pass `null` for `context`.
  If you're curious, you can read more in the [documentation for apply](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Function/apply).

## Bare Minimum Requirements

As is, the repository is missing code for most of the functions. It's your job
to fix the library by implementing them. The functions are split in two sections,
with a separate test suite for each.

The files in the `spec` directory contain the test suites. Your goal is to get all
the tests to pass by implementing the missing functions. Run all the tests by
opening `SpecRunner.html` in your browser.

The file `src/underbar.js` contains function definitions and explanations for
the following functions (*italicized functions* are solved for you). Implement
each of the functions by making all of the tests pass:

#### Part I:
- [ ] identity
- [ ] *first*
- [ ] last
- [ ] each
- [ ] *indexOf*
- [ ] filter
- [ ] reject
- [ ] uniq
- [ ] map
- [ ] *pluck*
- [ ] reduce

#### Part II:
- [ ] *contains*
- [ ] every
- [ ] some
- [ ] extend
- [ ] defaults
- [ ] *once*
- [ ] memoize
- [ ] delay
- [ ] shuffle

## Advanced Content

- [ ] invoke
- [ ] sortBy
- [ ] zip
- [ ] flatten
- [ ] intersection
- [ ] difference
- [ ] throttle

**Note:** Some browsers provide built-in functions--including `forEach`, `map`,
`reduce` and `filter`--that replicate the functionality of some of the functions
you will implement. Don't use them to implement your functions.

### Throttle

There's one function that is a little more complicated, so we've included some
more context to help you along.

**_.throttle(func, wait)**: Wrap a function `func` so that it can be called at
most once within a period of `wait` milliseconds. This is useful for throttling
access to expensive APIs or to drawing routines in a video game. Let's see how
it's used:

```javascript
var counter = 0;
var increment = function() {
  return counter += 1;
};

// Create a function called throttledIncrement. This function can be called at
// most once every 100ms
var throttledIncrement = _.throttle(increment, 100);

throttledIncrement(); // return 1; `counter` should now be 1
throttledIncrement(); // return 1; schedule `increment()` call in 100ms
throttledIncrement(); // return 1; should do nothing

// Wait 100 ms; `increment` is called
```

- Arguments passed to the throttled function should be passed to the original
  function.
- The throttled function should always return the most recently returned value of
  the original function.
- If the wait period is 100ms and the function was last called 30ms ago,
  another call to the throttled function should schedule a call for 0ms after the wait period is over.

## Nightmare Mode

### ES6

The *ECMAScript* specification is a scripting language specification upon which JavaScript implementations (such as those found in web browsers like Chrome) are based. In June 2015, the 6th edition of the ECMAScript standard was finalized, and is commonly referred to as ES6.

ES6 introduces a wealth of new features to JavaScript while being entirely reverse-compatible with older JavaScript. Even the most popular of web browsers like Chrome have a ton of work to do before all ES6 features are available, however, a lot of developers are using ES6 features and you should look forward to seeing more and more of ES6 in the next several years.

You can play around with ES6 in the latest version of Chrome.

- [ ] Visit `chrome://help` in Chrome and ensure that you are using version 49 or above. Once you're up to date with the latest version, Chrome will accept and run many new ES6 features, allowing you to attempt the refactor described next.

### Refactor with ES6 Arrow Functions and Rest parameters

ES6 introduces a slick new feature called *arrow function expressions* that provide syntactic sugar to make anonymous higher order functions (such as those you have been building out during this Underbar sprint) much more concise. Arrow function expressions also provide lexical scoping to the `this` value.

ES6 also provides a feature called *rest parameters* which provide syntactic sugar for making your work with function parameters much more appealing.

- [ ] Refactor your already-test-passing Underbar functions to helpfully utilize arrow function expressions and rest parameters. Assuming your refactors are correct, and that you have enabled experimental JavaScript in the step above, your tests will continue to pass
  - MDN is the source of truth for JavaScript. Refer to MDN's [arrow function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) and [rest parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters) documentation for reference and helpful information to get started.

*Important Note*: Again, our advanced content is intended to throw you in over your head. It is expected you feel underprepared for this particular task. Be strong and enjoy moving into the unknown. You will thrive in this industry if you learn to love learning with little support. Go make some mistakes, collaborate with your team, and figure it out. You got this!
