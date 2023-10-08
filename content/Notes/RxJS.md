---
date: 2023-10-07
tags:
  - webdev
---
## What is RxJS?

RxJS (Reactive Extensions for JavaScript) is a library for reactive programming using observables that makes it easier to compose asynchronous or callback-based code.

### Observables

The central component of RxJS is the Observable. An Observable represents a lazy push-based collection, either finite or infinite.

#### Creating an Observable


```
import { Observable } from 'rxjs';  const observable = new Observable(subscriber => {   subscriber.next(1);   subscriber.next(2);   subscriber.next(3);   subscriber.complete(); });
```
```

### Subscribing to Observables

You subscribe to an observable to execute it and catch the emitted values.

javascriptCopy code

``observable.subscribe({   next(x) { console.log(`Got value ${x}`); },   error(err) { console.error(`Something went wrong ${err}`); },   complete() { console.log('Done'); } });``

### Operators

Operators are pure functions built to work with observables. They allow you to handle complex manipulation of collections in a declarative manner.

#### Common Operators

1. `map`: Transforms the items emitted by an Observable.
2. `filter`: Filters out items based on a condition.
3. `mergeMap` / `switchMap`: Handles merging of multiple observables.

javascriptCopy code

`import { from } from 'rxjs'; import { map } from 'rxjs/operators';  const nums = from([1, 2, 3, 4, 5]); const squareNums = nums.pipe(map(n => n * n));`

### Subjects

A Subject is a special type of Observable that allows values to be multicast to many Observers.

javascriptCopy code

``import { Subject } from 'rxjs';  const subject = new Subject();  subject.subscribe({   next: (value) => console.log(`A: ${value}`) });  subject.subscribe({   next: (value) => console.log(`B: ${value}`) });  subject.next(1);  // Logs "A: 1" and "B: 1"``

## Advanced Topics

### Marble Testing

Marble Testing is an advanced technique to test observables by visually depicting the emitted values over a timeline.

### Higher-Order Observables

You can have Observables that emit Observables, leading to higher-order Observables. Operators like `mergeMap`, `switchMap`, and `concatMap` help to flatten these.

### Error Handling

Use the `catchError` operator to catch and handle errors gracefully.

## Best Practices

1. **Unsubscribing**: Always unsubscribe from observables to prevent memory leaks.
2. **Error Handling**: Always include error handling in your subscription logic.

## Resources

1. [RxJS Docs](https://rxjs.dev/guide/overview)
2. [Learn RxJS](https://www.learnrxjs.io/)
3. [RxJS GitHub Repo](https://github.com/ReactiveX/rxjs)