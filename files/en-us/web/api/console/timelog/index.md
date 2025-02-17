---
title: console.timeLog()
slug: Web/API/console/timeLog
page-type: web-api-instance-method
tags:
  - API
  - DOM
  - Debugging
  - Method
  - Web Development
  - web console
browser-compat: api.console.timeLog
---

{{APIRef("Console API")}}

{{AvailableInWorkers}}

The **`console.timeLog()`** method logs the current value of a timer that was previously started by calling {{domxref("console.time()")}}.

## Syntax

```js-nolint
timeLog()
timeLog(label)
```

### Parameters

- `label` {{optional_inline}}
  - : The name of the timer to log to the console. If this is omitted the label "default" is used.

### Return value

None ({{jsxref("undefined")}}).

## Description

The `console.timeLog()` method logs the current value of a timer.

The method can be passed the name of a timer. This will attempt to log the value of a timer created with that name in a previous call to {{domxref("console.time()")}}:

```js
console.time("reticulating splines");
reticulateSplines();
console.timeLog("reticulating splines");
// reticulating splines: 650ms
```

If the timer name is omitted, then the timer is named `"default"`:

```js
console.time();
reticulateSplines();
console.timeLog();
// default: 780ms
```

```js
console.time("default");
reticulateSplines();
console.timeLog();
// default: 780ms
```

If there is no corresponding timer, `timeLog()` logs a warning like:

```
Timer "timer name" doesn't exist.
```

See [Timers](/en-US/docs/Web/API/console#timers) in the documentation for more details and examples.

## Examples

```js
console.time("answer time");
alert("Click to continue");
console.timeLog("answer time");
alert("Do a bunch of other stuff…");
console.timeEnd("answer time");
```

The output from the example above shows the time taken by the user to dismiss the first
alert box, followed by the time it took for the user to dismiss the second alert:

```
answer time: 2542ms debugger eval code:3:9
answer time: 4161ms - timer ended
```

Notice that the timer's name is displayed when the timer value is logged using
`timeLog()` and again when it's stopped. In addition, the call to `timeEnd()`
has the additional information, "timer ended" to make it obvious that the timer is no
longer tracking time.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
