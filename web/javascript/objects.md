# Objects

## General info

In JavaScript an `Object` is a data type that actually represents a collection of data. It is a group of _key-value_ pairs that can store any other data type values, even other object. Example:

```js
const car = {
  wheels: 4,
  name: "Super Car",
  start() {
    console.log('We started moving')
  }
  stop: function() {
    console.log('We stopped moving')
  }
}
```

We declared an object. It can store different types of data at once. Variables `wheels` and `name` are called __properties__ of object. We can access them by using `.` operator on the left of the name of the object. Like this: `car.wheels`. `start()` and `stop()` are called a __methods__. Those are functions that can be invoked by accessing them just like properties: `car.start()`.

__Note!__ If you call `car.start`, it will only return the _function object_, because you need `()` to _invoke_ the function.

We can reassign values to there variables by accessing them like this:

```js
car.wheels = 5;
car[wheels] = 6;
```

__Note!__ Even though `car` is declared as a _constant_ we still can change it's contents (properties and methods). It is because we _mutate_ the object, not reassign it. We still __can't__ do `car = {}`, or `car = 2`.

## this keyword

The `this` keyword in a method refers to the object it belongs to. Example:

```js
var globaltest = 2
const testObject = {
  test: 3,
  showTest(test) {
    console.log(this.test)
  }
}
testObject.showTest(globaltest)
```

The code above will print `3` even though the parameter that method `showTest()` receives is called `test`. `this` keyword will present the object itself, so we can get `test` property of this object.

It can be confusing to understand what `this` refers to. But it is quite simple. We just need to look at the method call. It generally looks like this: `car.start()`. In this call we can see that method `start()` is called on the object `car`. So `this` in method `start()` will be pointing to the `car` object. That's it!

But there are occasions where methods are called differently. In this particular case, there is a _context_ for this method, because it is invoked directly on the `car` object. But what if we do this:

```js
const car = {
  wheels: 4,
  showWheels = function () {console.log(this.wheels)}
}

setTimeout(car.showWheels, 2000)
```

__Note!__ Pay attention to the absence of `()` at the end of the `showWheels`. Parenthases after a function name is what makes it an _function call_. We don't want to call this function right away, but _pass_ it as an _argument_ to the `setTimeout()`. `car.showWheels` will return a _function object_ that can be called later, in this example after 2 seconds. But the problem here is that this function object doesn't have any context. We are only passing the function itself, not antire object. You can imagine that there is something like this in the `setTimeout` function declaration:

```js
const setTimeout(func, timeout) {
  // after timeout time
  func()
}
```

As you can see, there is not `.` and object name to rely on. That's why `this` will fall through and point to the `global` object instead. 
__Note!__ In a _strict mode_, when `this` can't find a proper context, it will return `undefined`.

One of the ways of solving this particular problem is creating an anonymous function right in the `setTimeout` call:

```js
setTimeout(() => {car.showWheels()}, 2000)
```

`() => {}` allows us to create an anonymous function and in JavaScript, when you create such function somewhere it will return this function's object in it's place. So now `setTimeout` will have a function with `car.showWheels()` call in it's body. `showWheels()` will have a proper context and everything will work just fine.

