# SYNOPSIS
A minimalist event emitter for C++14.

# DESCRIPTION
Event emitters are handy for evented programming, `node.js`/`io.js` 
has a [`nice one`](https://iojs.org/api/events.html).
This one is similar, but with a few less features. This emitter
allows you to emit and receive arbitrary/variadic paramaters of 
equal type.

# BUILD STATUS
![build-status](https://travis-ci.org/hij1nx/cpp-eventemitter.svg)

# EXAMPLE

```cc
#include "events.h"

int main() {

  EventEmitter ee;

  ee.on("hello", [](string name, int num) {
    // ...do something with the values.
  });

  ee.emit("hello", "beautiful", 100);
}
```

# API

## INSTANCE METHODS

### `void` on(string eventName, lambda callback);
Listen for an event multiple times, add as many as you want.

### `void` once(string eventName, lambda callback);
Listen for an event only once.

### `void` emit(string eventName [, arg1 [, arg2...]]);
Emit data for a particular event.

### `void` off(string eventName);
Remove listener for a particular event.

### `void` off();
Remove all listeners on the emitter.

### `int` listeners();
Find out how many listeners had been added to an emitter.

### `int` listeners(string eventName);
Find out how many listeners had been added to an emitter
for a particular event.

## INSTANCE MEMBERS

### maxListeners
How many listeners an event emitter should have
before considering that there is a memory leak.

