# RXJS

# Introduction

Observables are a fundamental concept in RxJS. They represent a stream of values or events over time. In other words, an observable is a sequence of data that can be observed and reacted to. It can emit multiple values asynchronously, including values, errors, and completion signals.

Observables are used to handle asynchronous and event-based programming by providing a way to manage and manipulate data streams. They can be created from various sources such as user interactions, network requests, timers, or existing data structures.

Observables have three main characteristics:

1. Data Producer: Observables are responsible for producing and emitting values or events over time.
2. Lazy: Observables are lazy by nature. They don't start emitting values until there is a subscriber.
3. Cancellation: Observables can be canceled or unsubscribed from, allowing you to control the lifecycle of the data stream.

Observables can be transformed, combined, and manipulated using various operators provided by RxJS, enabling powerful data manipulation and composition. They also support a wide range of features like filtering, mapping, merging, combining, and more.

To summarize, observables are the core building blocks of reactive programming in RxJS, providing a way to handle asynchronous and event-based data streams.

# How to create observables (Basics)

RxJS provides several methods to create observables from different sources. Here are some common ways to create observables:

1. Creating an Observable from an Array:
    
    ```jsx
    import { of } from 'rxjs';
    
    const array = [1, 2, 3, 4, 5];
    const arrayObservable = of(...array);
    arrayObservable.subscribe(value => console.log(value));
    
    ```
    
2. Creating an Observable from an Event:
    
    ```jsx
    import { fromEvent } from 'rxjs';
    
    const button = document.getElementById('myButton');
    const buttonClickObservable = fromEvent(button, 'click');
    buttonClickObservable.subscribe(event => console.log(event));
    
    ```
    
3. Creating an Observable from a Promise:
    
    ```jsx
    import { from } from 'rxjs';
    
    const promise = new Promise(resolve => resolve('Hello, RxJS!'));
    const promiseObservable = from(promise);
    promiseObservable.subscribe(value => console.log(value));
    
    ```
    
4. Creating a Custom Observable:
You can create a custom observable using the `Observable` constructor and providing a subscribe function. The subscribe function defines how the observable will emit values or events.
    
    ```jsx
    import { Observable } from 'rxjs';
    
    const customObservable = new Observable(observer => {
      observer.next(1);
      observer.next(2);
      observer.next(3);
      observer.complete();
    });
    
    customObservable.subscribe(value => console.log(value));
    
    ```
    

These are just a few examples of how to create observables from different sources. RxJS offers many more creation operators and methods to create observables from timers, AJAX requests, WebSocket connections, and more.

# All different ways to create observables

Certainly! Here are some of the different ways to create observables in RxJS:

1. Creation Operators:
    - `of`: Creates an observable that emits a sequence of values.
    - `from`: Converts an array, iterable, promise, or other observable-like objects into an observable.
    - `interval`: Emits incremental numbers at a specified interval.
    - `timer`: Emits a value after a specified delay or at regular intervals.
    - `fromEvent`: Creates an observable from DOM events or Node.js EventEmitter.
    - `ajax`: Creates an observable from AJAX requests.
    - `create`: Creates a custom observable using the `Observable` constructor.
2. Subject:
    - `Subject`: Represents a special type of observable that can act as both an observer and an observable. It allows multicasting to multiple subscribers.
3. Combining Observables:
    - `combineLatest`: Combines multiple observables into a single observable that emits an array of the latest values from each source observable.
    - `concat`: Concatenates multiple observables sequentially, emitting values in the order they are provided.
    - `merge`: Merges multiple observables into a single observable, emitting values as they are emitted from any source observable.
    - `zip`: Combines multiple observables into a single observable by emitting values pairwise based on their order.
4. Transformation Operators:
    - `map`: Applies a projection function to each value emitted by the source observable.
    - `filter`: Filters values emitted by the source observable based on a condition.
    - `reduce`: Accumulates values emitted by the source observable and emits the accumulated result.
5. Error Handling:
    - `catchError`: Catches errors thrown by the source observable and replaces them with a new observable or value.
    - `retry`: Resubscribes to the source observable when it encounters an error, allowing for retry attempts.

These are just a few examples of the different ways to create and manipulate observables in RxJS. The library provides a rich set of operators and methods to handle various use cases and scenarios.

---

## 1.  Creation Operators

Certainly! Here are examples of using the creation operators `of`, `from`, `interval`, `timer`, `fromEvent`, `ajax`, and `create`:

1. `of`:
    
    ```jsx
    import { of } from 'rxjs';
    
    const values = of(1, 2, 3, 4, 5);
    values.subscribe(value => console.log(value));
    // Output: 1, 2, 3, 4, 5
    ```
    
2. `from`:
    
    ```jsx
    import { from } from 'rxjs';
    
    const array = [1, 2, 3, 4, 5];
    const arrayObservable = from(array);
    arrayObservable.subscribe(value => console.log(value));
    // Output: 1, 2, 3, 4, 5
    
    const promise = new Promise(resolve => resolve('Hello, RxJS!'));
    const promiseObservable = from(promise);
    promiseObservable.subscribe(value => console.log(value));
    // Output: Hello, RxJS!
    ```
    
3. `interval`:
    
    ```jsx
    import { interval } from 'rxjs';
    
    const source = interval(1000);
    source.subscribe(value => console.log(value));
    // Output: 0, 1, 2, 3, 4, ...
    ```
    
4. `timer`:
    
    ```jsx
    import { timer } from 'rxjs';
    
    const source = timer(2000, 1000); // Delay of 2 seconds, then emit every 1 second
    source.subscribe(value => console.log(value));
    // Output: 0, 1, 2, 3, 4, ...
    ```
    
5. `fromEvent`:
    
    ```jsx
    import { fromEvent } from 'rxjs';
    
    const button = document.getElementById('myButton');
    const buttonClickObservable = fromEvent(button, 'click');
    buttonClickObservable.subscribe(event => console.log(event));
    // Output: MouseEvent object when the button is clicked
    
    ```
    
6. `ajax`:
    
    ```jsx
    import { ajax } from 'rxjs/ajax';
    
    const url = '<https://api.example.com/data>';
    const ajaxObservable = ajax.getJSON(url);
    ajaxObservable.subscribe(data => console.log(data));
    // Output: Data received from the API endpoint
    
    ```
    
7. `create`:
    
    ```jsx
    import { Observable } from 'rxjs';
    
    const customObservable = new Observable(observer => {
      observer.next(1);
      observer.next(2);
      observer.next(3);
      observer.complete();
    });
    
    customObservable.subscribe(value => console.log(value));
    // Output: 1, 2, 3
    ```
    

These examples demonstrate how to create observables using various creation operators in RxJS.

---

## 2.  Using ‘Subject’

Certainly! Here's an example of using a `Subject` in RxJS:

```jsx
import { Subject } from 'rxjs';

// Create a new Subject
const subject = new Subject();

// Subscribe to the Subject
subject.subscribe(value => console.log('Subscriber A:', value));

// Emit values to the Subject
subject.next(1); // Output: Subscriber A: 1
subject.next(2); // Output: Subscriber A: 2

// Subscribe another subscriber to the Subject
subject.subscribe(value => console.log('Subscriber B:', value));

// Emit values to the Subject again
subject.next(3);
subject.next(4);
// Output: Subscriber A: 3
// Output: Subscriber B: 3
// Output: Subscriber A: 4
// Output: Subscriber B: 4

// Complete the Subject
subject.complete();

// Subscriber C won't receive any values after completion
subject.subscribe(value => console.log('Subscriber C:', value));
// Output: Subscriber C: 1 (if it subscribed before the completion)

```

In this example, we create a `Subject` called `subject`. We then subscribe two subscribers, "Subscriber A" and "Subscriber B," to the `subject`. When we call `subject.next(value)`, it emits the value to all the subscribed subscribers. So both "Subscriber A" and "Subscriber B" receive the emitted values.

Afterward, we subscribe "Subscriber C" to the `subject`, but since the `subject` has already completed, it won't receive any further values.

`Subject` is particularly useful when you want to multicast values to multiple subscribers, allowing them to receive the same set of emitted values.

<aside>
💡 It's worth noting that there are other variations of subjects in RxJS, such as `BehaviorSubject`, `ReplaySubject`, and `AsyncSubject`,
 which have additional features like maintaining the latest value, 
replaying past values, or only emitting the final value, respectively. 
These variations offer more specialized use cases depending on your 
requirements.

</aside>

Certainly! Here's an explanation of `BehaviorSubject`, `ReplaySubject`, and `AsyncSubject`, along with examples for each:

1. **BehaviorSubject**:
    - `BehaviorSubject` is a variation of `Subject` that holds a current value and emits it to new subscribers. It remembers the latest value and immediately provides it to any new subscriber.
    - When a new subscriber subscribes to a `BehaviorSubject`, it receives the last emitted value or the initial value if no values have been emitted yet.
    - `BehaviorSubject` also emits new values to its subscribers, just like a regular `Subject`.
    - Example:
    
    ```jsx
    import { BehaviorSubject } from 'rxjs';
    
    // Create a BehaviorSubject with an initial value of 0
    const subject = new BehaviorSubject(0);
    
    // Subscribe to the BehaviorSubject
    subject.subscribe(value => console.log('Subscriber A:', value));
    
    // Output: Subscriber A: 0
    
    // Emit a new value
    subject.next(1);
    
    // Output: Subscriber A: 1
    
    // Subscribe a new subscriber
    subject.subscribe(value => console.log('Subscriber B:', value));
    
    // Output: Subscriber B: 1 (receives the latest value immediately)
    
    ```
    
2. **ReplaySubject**:
    - `ReplaySubject` is a variation of `Subject` that remembers a specified number of previously emitted values and replays them to new subscribers.
    - When a new subscriber subscribes to a `ReplaySubject`, it receives a defined number of past values emitted by the `ReplaySubject`.
    - The number of past values to be replayed is specified when creating the `ReplaySubject`.
    - Example:
    
    ```jsx
    import { ReplaySubject } from 'rxjs';
    
    // Create a ReplaySubject that replays the last 2 values
    const subject = new ReplaySubject(2);
    
    // Emit values to the ReplaySubject
    subject.next(1);
    subject.next(2);
    subject.next(3);
    
    // Subscribe to the ReplaySubject
    subject.subscribe(value => console.log('Subscriber:', value));
    
    // Output: Subscriber: 2 (replays the last 2 emitted values)
    // Output: Subscriber: 3
    
    // Emit another value
    subject.next(4);
    
    // Output: Subscriber: 4
    
    ```
    
3. **AsyncSubject**:
    - `AsyncSubject` is a variation of `Subject` that only emits the last value when it completes. It waits until the `complete()` method is called to emit the final value, discarding any previous values.
    - `AsyncSubject` is useful when you only need the final value from an asynchronous operation or stream.
    - Example:
    
    ```jsx
    import { AsyncSubject } from 'rxjs';
    
    // Create an AsyncSubject
    const subject = new AsyncSubject();
    
    // Subscribe to the AsyncSubject
    subject.subscribe(value => console.log('Subscriber:', value));
    
    // Output: (no output yet)
    
    // Emit values to the AsyncSubject
    subject.next(1);
    subject.next(2);
    subject.next(3);
    
    // Complete the AsyncSubject
    subject.complete();
    
    // Output: Subscriber: 3 (emits the final value after completion)
    
    ```
    

These variations of `Subject` provide specialized functionalities to cater to different use cases. Understanding their behavior and characteristics allows you to choose the appropriate subject type based on your specific requirements.

<aside>
💡 Some Use Case

1. **BehaviorSubject** :
    - User Authentication: You can use a `BehaviorSubject` to store the authentication status of a user. Any component that needs access to the user's authentication status can subscribe to the `BehaviorSubject` and receive the latest authentication status immediately upon subscription.
2. **ReplaySubject** :
    - Caching and History: If you have a scenario where you want new subscribers to receive a certain number of past values, such as caching or maintaining a history of events, `ReplaySubject` can be useful. For example, you can use it to store and replay the last few events of user interactions or system logs for new subscribers.
3. **AsyncSubject** :
    - HTTP Requests: `AsyncSubject` is useful when you want to fetch data from an HTTP request and emit only the final result. It ensures that subscribers only receive the last emitted value when the request is complete, making it suitable for scenarios where you only need the final response.
    - Long-Running Operations: If you have an operation that takes time to complete, such as processing a large file or performing complex calculations, `AsyncSubject` allows you to emit the final result when the operation is done. This can be helpful in cases where you want to wait for the operation to complete before taking further actions.
    - Promises to Observables: When converting Promises to Observables, `AsyncSubject` can be used to emit a single value from the Promise when it resolves. Subscribers to the `AsyncSubject` will receive that value when the Promise completes.
</aside>

---

# More on Observable and Subject

<aside>
💡 The main difference between `new Observable` and `Subject` lies in their behavior and use cases:

1. `new Observable`:
    - `Observable` is a basic building block in RxJS that represents a stream of values over time.
    - When you create an `Observable` using `new Observable`, you define the logic for producing values and emitting them to subscribers.
    - Each subscriber to an `Observable` gets its own independent execution of the observable logic.
    - Subscribers to an `Observable` receive values emitted after they subscribe.
    - `Observable` is suitable when you want to create custom data streams, control their behavior, and have independent execution for each subscriber.
2. `Subject`:
    - `Subject` is a special type of observable that can act as both an observer and an observable.
    - It allows multicasting, meaning that multiple subscribers can listen to the same `Subject`, and they all receive the same set of emitted values.
    - `Subject` does not replay past values to new subscribers. It only emits values that occur after subscription.
    - `Subject` provides a way to broadcast and share values among multiple subscribers.
    - It is commonly used in scenarios where you need to create event buses, handle inter-component communication, or implement pub/sub patterns.
</aside>

<aside>
💡 Real-life use cases:

- Use `new Observable` when you want to create custom asynchronous data streams, such as handling AJAX requests, reading from files, or processing data from external sources. You can define the logic for emitting values, handling errors, and completing the stream based on your specific requirements.
- Use `Subject` when you need to implement event-driven architectures, inter-component communication, or pub/sub patterns. For example, you can use a `Subject` to create an event bus that allows different components or services to communicate and exchange information. Each component can subscribe to the `Subject` and receive the same events or messages.
</aside>

### Observable :

Certainly! Here's an example that demonstrates how each subscriber to an `Observable` gets its own independent execution of the observable logic:

```jsx
import { Observable } from 'rxjs';

// Create an Observable
const observable = new Observable(observer => {
  console.log('Observable logic started');
  let count = 0;

  const intervalId = setInterval(() => {
    observer.next(count++);
  }, 1000);

  return () => {
    console.log('Observable logic stopped');
    clearInterval(intervalId);
  };
});

// Subscribe to the Observable with Subscriber A
const subscriberA = observable.subscribe(value => {
  console.log('Subscriber A:', value);
});

// After 3 seconds, subscribe to the Observable with Subscriber B
setTimeout(() => {
  const subscriberB = observable.subscribe(value => {
    console.log('Subscriber B:', value);
  });
}, 3000);

```

In this example, we create an `Observable` that emits incrementing values every second using `observer.next()`. Each subscriber to the `Observable` will receive these values independently.

When we subscribe with "Subscriber A", the observable logic starts, and it logs `'Observable logic started'`. "Subscriber A" starts receiving values emitted by the observable.

After 3 seconds, we subscribe with "Subscriber B". At this point, a new independent execution of the observable logic starts, and "Subscriber B" will receive values separately from "Subscriber A".

If we were to unsubscribe "Subscriber A" or "Subscriber B" by calling `subscriberA.unsubscribe()` or `subscriberB.unsubscribe()`, respectively, the corresponding observable logic would stop, and it would log `'Observable logic stopped'`.

This example illustrates that each subscriber to an `Observable` has its own independent execution of the observable logic. They can receive values concurrently and unsubscribe individually without affecting other subscribers.

This is what output looks like 👇

![Untitled](RXJS%20eb49aca6504a4806b394eb18df3d05f0/Untitled.png)

### Subject :

1. Centralized Event Bus: `Subject` allows you to create a centralized event bus or message broker where different parts of your application can publish and subscribe to events. It enables decoupled communication between components or services.
2. Late Subscription: With `Subject`, you can subscribe to it at any point in time and still receive the latest values emitted. This can be useful when you want to ensure that a subscriber receives the most up-to-date information, even if they subscribe after some events have already occurred.
3. Manual Control: `Subject` provides explicit methods to emit values (`next`), handle errors (`error`), and mark the completion of the stream (`complete`). This gives you more control over when and how values are emitted to subscribers.
4. Broadcasting to Multiple Subscribers: Unlike regular `Observable`, where each subscriber gets an independent execution of the observable logic, `Subject` allows you to broadcast the same set of values to multiple subscribers simultaneously.
5. State Management: `Subject` can be used as a simple state management tool, where subscribers receive updates whenever the state changes. This can be useful for scenarios where multiple components need to stay in sync with a shared state.

---

## 3.  Combining Observables

Certainly! Here are examples of combining observables using `combineLatest`, `concat`, `merge`, and `zip`:

1. **combineLatest** :
    - `combineLatest` combines multiple observables into a single observable that emits an array of the latest values from each source observable whenever any of the source observables emit a new value.
    - Example:
    
    ```jsx
    import { combineLatest, interval } from 'rxjs';
    
    const observable1 = interval(1000); // Emits values 0, 1, 2, ...
    const observable2 = interval(2000); // Emits values 0, 1, 2, ...
    
    const combined = combineLatest([observable1, observable2]);
    
    combined.subscribe(([value1, value2]) => {
      console.log('Combined:', value1, value2);
    });
    
    // Output:
    // Combined: 0 0
    // Combined: 1 0
    // Combined: 1 1
    // Combined: 2 1
    // Combined: 2 2
    // ...
    ```
    
2. **concat** :
    - `concat` concatenates multiple observables sequentially, emitting values in the order they are provided. It subscribes to each observable one after another, waiting for each to complete before moving to the next.
    - Example:
    
    ```jsx
    import { concat, interval } from 'rxjs';
    import { take } from 'rxjs/operators';
    
    const observable1 = interval(1000).pipe(take(3)); // Emits values 0, 1, 2
    const observable2 = interval(500).pipe(take(2)); // Emits values 0, 1
    
    const concatenated = concat(observable1, observable2);
    
    concatenated.subscribe(value => {
      console.log('Concatenated:', value);
    });
    
    // Output:
    // Concatenated: 0
    // Concatenated: 1
    // Concatenated: 2
    // Concatenated: 0
    // Concatenated: 1
    ```
    
3. **merge** :
    - `merge` merges multiple observables into a single observable, emitting values as they are emitted from any source observable. Values from different observables can interleave.
    - Example:
    
    ```jsx
    import { merge, interval } from 'rxjs';
    
    const observable1 = interval(1000); // Emits values 0, 1, 2, ...
    const observable2 = interval(1500); // Emits values 0, 1, 2, ...
    
    const merged = merge(observable1, observable2);
    
    merged.subscribe(value => {
      console.log('Merged:', value);
    });
    
    // Output:
    // Merged: 0
    // Merged: 0
    // Merged: 1
    // Merged: 2
    // Merged: 1
    // Merged: 3
    // ...
    ```
    
4. **zip :**
    - `zip` combines multiple observables into a single observable by emitting values pairwise based on their order. It waits for all source observables to emit a value before emitting an array of the combined values.
    - Example:
    
    ```jsx
    import { zip, interval } from 'rxjs';
    import { take } from 'rxjs/operators';
    
    const observable1 = interval(1000).pipe(take(3)); // Emits values 0, 1, 2
    const observable2 = interval(1500).pipe(take(3)); // Emits values 0, 1, 2
    
    const zipped = zip(observable1, observable2);
    
    zipped.subscribe(([value1, value2]) => {
    	console.log('Zipped:', value1, value2);
    });
    
    // Output:
    // Zipped: 0 0
    // Zipped: 1 1
    // Zipped: 2 2
    ```
    

Some More down here 👇

1. `forkJoin`: 
    
    Waits for all source observables to complete and  then emits an array of the last values from each observable. It is used when you need to combine the results of multiple observables into a single emission.
    
    ```jsx
    import { forkJoin, of, timer } from 'rxjs';
    
    const observable1 = of('Hello');
    const observable2 = of('World');
    const observable3 = timer(2000);
    
    forkJoin([observable1, observable2, observable3]).subscribe(([value1, value2]) => {
      console.log('ForkJoined:', value1, value2);
    });
    
    // Output:
    // ForkJoined: Hello World (after 2 seconds)
    
    ```
    
2. `race`:
    
    Takes multiple observables and emits the values from 
    the observable that emits first. It is used when you want to take the 
    value from the observable that responds first and ignore the rest.
    
    ```jsx
    import { race, interval } from 'rxjs';
    
    const observable1 = interval(1000);
    const observable2 = interval(1500);
    
    race(observable1, observable2).subscribe(value => {
      console.log('Race:', value);
    });
    
    // Output:
    // Race: 0 (from the faster observable)
    // Race: 1
    // Race: 2
    // ...
    ```
    
3. `withLatestFrom`:
    
    Combines the latest values from the source 
    observable with values from other observables, producing a new value 
    whenever the source observable emits. It is used when you need to 
    combine the latest values from multiple observables and perform some 
    logic based on those values.
    
    ```jsx
    import { withLatestFrom, interval } from 'rxjs';
    
    const source = interval(1000);
    const secondObservable = interval(2000);
    
    source.pipe(withLatestFrom(secondObservable)).subscribe(([value1, value2]) => {
      console.log('WithLatestFrom:', value1, value2);
    });
    
    // Output:
    // WithLatestFrom: 0 0
    // WithLatestFrom: 1 0
    // WithLatestFrom: 2 1
    // WithLatestFrom: 3 1
    // ...
    ```
    
4. `startWith`:
    
    Prepends a specified value to the sequence of 
    values emitted by the source observable. It is used when you want to add
     an initial value before the observable starts emitting its regular 
    values.
    
    ```jsx
    import { of } from 'rxjs';
    import { startWith } from 'rxjs/operators';
    
    const source = of('World');
    
    source.pipe(startWith('Hello')).subscribe(value => {
      console.log('StartWith:', value);
    });
    
    // Output:
    // StartWith: Hello
    // StartWith: World
    ```
    
5. `combineAll`:
    
    Combines a higher-order observable by emitting 
    an array of the most recent values from each nested observable when any 
    of the nested observables emit a value. It is used when you have an 
    observable that emits other observables, and you want to combine the 
    latest values from each nested observable.
    
    ```jsx
    import { combineAll, interval, take } from 'rxjs';
    
    const source = interval(1000).pipe(take(3));
    const higherOrderObservable = source.pipe(map(value => interval(500).pipe(take(2))));
    
    higherOrderObservable.pipe(combineAll()).subscribe(value => {
      console.log('CombineAll:', value);
    });
    
    // Output:
    // CombineAll: [0, 0]
    // CombineAll: [1, 0]
    // CombineAll: [2, 0]
    ```
    
6. `switch`:
    
    Converts a higher-order observable into a first-order observable by subscribing to the most recently emitted inner observable and emitting its values. It is used when you have an observable that emits other observables, and you want to switch to the latest emitted observable and receive its values.
    
    ```jsx
    import { interval, of } from 'rxjs';
    import { switchAll } from 'rxjs/operators';
    
    const source = interval(1000).pipe(take(3));
    const higherOrderObservable = source.pipe(map(value => interval(500).pipe(take(2))));
    
    higherOrderObservable.pipe(switchAll()).subscribe(value => {
      console.log('Switched:', value);
    });
    
    // Output:
    // Switched: 0 (from the first inner observable)
    // Switched: 1
    // Switched: 0 (from the second inner observable)
    // Switched: 1
    
    ```
    
7. `exhaust`:
    
    Ignores new source observables while an inner observable is still active. Once the active inner observable completes, it subscribes to the next available inner observable. It is used when you want to ignore new observables until the current inner observable completes.
    
    ```jsx
    import { interval } from 'rxjs';
    import { exhaust, take } from 'rxjs/operators';
    
    const source = interval(1000).pipe(take(3));
    const higherOrderObservable = source.pipe(map(value => 
    	interval(500).pipe(take(2))
    ));
    
    higherOrderObservable.pipe(exhaust()).subscribe(value => {
    	console.log('Exhausted:', value);
    });
    
    // Output:
    // Exhausted: 0 (from the first inner observable)
    // Exhausted: 1
    // Exhausted: 2
    ```
    
8. `mergeMap` (or `flatMap`):
    
    Maps each value from the source observable to an inner observable, subscribes to all inner observables, and emits values from all of them. It is used when you need to map values to inner observables and combine their emissions into a single observable stream.
    
    ```jsx
    import { of } from 'rxjs';
    import { mergeMap } from 'rxjs/operators';
    
    const source = of('Hello', 'World');
    
    source.pipe(mergeMap(value => of(`${value}!`))).subscribe(value => {
      console.log('Merged:', value);
    });
    
    // Output:
    // Merged: Hello!
    // Merged: World!
    ```
    

1. `concatMap`:
    
    Maps each value from the source observable to an inner observable, subscribes to them sequentially, and emits values in the order they are emitted by the inner observables. It is used when you want to preserve the order of emissions from the inner observables.
    
    ```jsx
    import { interval } from 'rxjs';
    import { concatMap, take } from 'rxjs/operators';
    
    const source = interval(1000).pipe(take(3));
    
    source.pipe(concatMap(value => interval(500).pipe(take(2)))).subscribe(value => {
      console.log('Concatenated:', value);
    });
    
    // Output:
    // Concatenated: 0 (from the first inner observable)
    // Concatenated: 1
    // Concatenated: 0 (from the second inner observable)
    // Concatenated: 1
    ```
    
2. `switchMap`:
    
    Maps each value from the source observable to an inner observable, subscribes to the inner observable, and emits values from the most recently subscribed inner observable. It is used when you want to switch to a new inner observable whenever a new value arrives, canceling the previous inner observable subscription.
    
    ```jsx
    import { interval } from 'rxjs';
    import { switchMap, take } from 'rxjs/operators';
    
    const source = interval(1000).pipe(take(3));
    
    source.pipe(switchMap(value => interval(500).pipe(take(2)))).subscribe(value => {
      console.log('Switched:', value);
    });
    
    // Output:
    // Switched: 0 (from the first inner observable)
    // Switched: 1
    // Switched: 0 (from the second inner observable)
    // Switched: 1
    
    ```
    

---

## 4. Transformation Operators

1. `map`: Applies a projection function to each value emitted by the source observable and emits the transformed values.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { map } from 'rxjs/operators';
    
    const source = of(1, 2, 3);
    
    source.pipe(map(value => value * 2)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 2
    // 4
    // 6
    ```
    
2. `pluck`: Retrieves a specified nested property from each value emitted by the source observable.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { pluck } from 'rxjs/operators';
    
    const source = of({ name: 'John', age: 30 }, { name: 'Jane', age: 25 });
    
    source.pipe(pluck('name')).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // John
    // Jane
    
    ```
    
3. `mapTo`: Maps every value emitted by the source observable to a constant value.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { mapTo } from 'rxjs/operators';
    
    const source = of(1, 2, 3);
    
    source.pipe(mapTo('Hello')).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // Hello
    // Hello
    // Hello
    
    ```
    
4. `filter`: Filters values emitted by the source observable based on a condition. Only the values that satisfy the condition are passed through to the resulting observable.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { filter } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(filter(value => value % 2 === 0)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 2
    // 4
    ```
    
5. `take`: Takes a specified number of values emitted by the source observable and completes the observable.
Example:
    
    ```jsx
    import { interval } from 'rxjs';
    import { take } from 'rxjs/operators';
    
    const source = interval(1000);
    
    source.pipe(take(3)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 0
    // 1
    // 2
    ```
    
6. `takeLast`: Takes the last specified number of values emitted by the source observable and completes the observable.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { takeLast } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(takeLast(3)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 3
    // 4
    // 5
    ```
    
7. `takeWhile`: Takes values emitted by the source observable until the provided condition becomes false. It completes the observable when the condition fails.
Example:
    
    ```jsx
    import { interval } from 'rxjs';
    import { takeWhile } from 'rxjs/operators';
    
    const source = interval(1000);
    
    source.pipe(takeWhile(value => value < 5)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 0
    // 1
    // 2
    // 3
    // 4
    ```
    
8. `takeUntil`: Takes values emitted by the source observable until another observable emits a value. It completes the observable when the other observable emits.
Example:
    
    ```jsx
    import { interval, timer } from 'rxjs';
    import { takeUntil } from 'rxjs/operators';
    
    const source = interval(1000);
    const timerObservable = timer(5000);
    
    source.pipe(takeUntil(timerObservable)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 0
    // 1
    // 2
    // 3
    // 4
    ```
    

1. `first`: Emits only the first value emitted by the source observable and completes the observable.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { first } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(first()).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    ```
    
2. `last`: Emits only the last value emitted by the source observable and completes the observable.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { last } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(last()).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 5
    ```
    
3. `skip`:  Skips a specified number of values emitted by the source observable and emits the rest.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { skip } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(skip(2)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 3
    // 4
    // 5
    
    ```
    
4. `skipLast`: Skips the last specified number of values emitted by the source observable and emits the rest.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { skipLast } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(skipLast(2)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 2
    // 3
    ```
    
5. `skipWhile`: Skips values emitted by the source observable until the provided condition becomes false, and emits the rest.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { skipWhile } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(skipWhile(value => value < 3)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 3
    // 4
    // 5
    ```
    
6. `skipUntil`: Skips values emitted by the source observable until another observable emits a value, and emits the rest.
Example:
    
    ```jsx
    import { interval, timer } from 'rxjs';
    import { skipUntil } from 'rxjs/operators';
    
    const source = interval(1000);
    const timerObservable = timer(3000);
    
    source.pipe(skipUntil(timerObservable)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 2
    // 3
    // 4
    // ...
    
    ```
    
7. `distinct`: Filters out duplicate consecutive values emitted by the source observable.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { distinct } from 'rxjs/operators';
    
    const source = of(1, 2, 2, 3, 3, 3, 4, 5, 5);
    
    source.pipe(distinct()).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 2
    // 3
    // 4
    // 5
    
    ```
    
8. `distinctUntilChanged`: Filters out consecutive values emitted by the source observable that are equal to the previous value.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { distinctUntilChanged } from 'rxjs/operators';
    
    const source = of(1, 1, 2, 2, 3, 4, 4, 5, 5);
    
    source.pipe(distinctUntilChanged()).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 2
    // 3
    // 4
    // 5
    
    ```
    
9. `distinctUntilKeyChanged`: Filters out consecutive values emitted by the source observable based on a specified key's equality comparison.
Example:
    
    ```jsx
    import { of }
    from 'rxjs';
    import { distinctUntilKeyChanged } from 'rxjs/operators';
    
    const source = of(
    { id: 1, name: 'John' },
    { id: 2, name: 'John' },
    { id: 2, name: 'Jane' },
    { id: 3, name: 'Jane' }
    );
    
    source.pipe(distinctUntilKeyChanged('name')).subscribe(result => {
    console.log(result);
    });
    
    // Output:
    // { id: 1, name: 'John' }
    // { id: 2, name: 'Jane' }
    ```
    

1. `debounceTime`: Emits a value from the source observable only after a specified time has passed without any new values being emitted.
Example:
    
    ```jsx
    import { fromEvent } from 'rxjs';
    import { debounceTime } from 'rxjs/operators';
    
    const button = document.getElementById('button');
    const clicks = fromEvent(button, 'click');
    
    clicks.pipe(debounceTime(1000)).subscribe(() => {
      console.log('Clicked after 1 second of inactivity');
    });
    
    // Output:
    // Clicked after 1 second of inactivity
    ```
    

1. `throttleTime`: Emits the first value from the source observable, and then ignores subsequent values for a specified time period.
Example:
    
    ```jsx
    import { interval } from 'rxjs';
    import { throttleTime } from 'rxjs/operators';
    
    const source = interval(1000);
    
    source.pipe(throttleTime(2000)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 0
    // 3
    // 6
    // ...
    ```
    
2. `buffer`: Collects multiple values emitted by the source observable and emits them as an array whenever a specified signal observable emits.
Example:
    
    ```jsx
    import { interval, fromEvent } from 'rxjs';
    import { buffer } from 'rxjs/operators';
    
    const source = interval(1000);
    const clickSignal = fromEvent(document, 'click');
    
    source.pipe(buffer(clickSignal)).subscribe(result => {
      console.log(result);
    });
    
    // Output (When clicking the document):
    // [0, 1, 2]
    // [3, 4, 5, 6]
    // [7, 8]
    // ...
    ```
    

1. `bufferTime`: Collects values emitted by the source observable over a specified time period and emits them as an array.
Example:
    
    ```jsx
    import { interval } from 'rxjs';
    import { bufferTime } from 'rxjs/operators';
    
    const source = interval(1000);
    
    source.pipe(bufferTime(3000)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // [0, 1, 2]
    // [3, 4, 5]
    // [6, 7, 8]
    // ...
    
    ```
    
2. `scan`: Applies an accumulator function to the values emitted by the source observable and emits the accumulated result after each emission.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { scan } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(scan((acc, value) => acc + value)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 3
    // 6
    // 10
    // 15
    ```
    
3. `reduce`: Accumulates values emitted by the source observable and emits the accumulated result.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { reduce } from 'rxjs/operators';
    
    const source = of(1, 2, 3, 4, 5);
    
    source.pipe(reduce((acc, value) => acc + value)).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 15
    ```
    

---

## 5. Error Handling

1. `catchError`: Catches errors emitted by the source observable and replaces them with a fallback observable or value.
Example:
    
    ```jsx
    import { of, throwError } from 'rxjs';
    import { catchError } from 'rxjs/operators';
    
    const source = of(1, 2, 3, throwError('Error'), 5);
    
    source.pipe(
      catchError(error => {
        console.log('Caught error:', error);
        return of('Fallback Value');
      })
    ).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 2
    // 3
    // Caught error: Error
    // Fallback Value
    // 5
    ```
    
    Use case: `catchError` is commonly used to handle errors gracefully and provide fallback behavior. It allows you to handle specific error scenarios and recover by returning a fallback observable or value.
    
2. `retry`: Resubscribes to the source observable when it encounters an error, allowing for retry attempts.
Example:
    
    ```jsx
    import { of, throwError } from 'rxjs';
    import { retry } from 'rxjs/operators';
    
    let attempts = 0;
    
    const source = of('Initial Value', throwError('Error')).pipe(
      retry(3)
    );
    
    source.subscribe(
      result => console.log(result),
      error => console.log('Caught error after retry attempts:', error)
    );
    
    // Output:
    // Initial Value
    // Initial Value
    // Initial Value
    // Caught error after retry attempts: Error
    ```
    
    Use case: `retry` is useful in scenarios where you want to retry the execution of an observable sequence after encountering an error. It allows for a specified number of retry attempts to handle temporary failures or intermittent errors.
    
3. `retryWhen`: Resubscribes to the source observable when it encounters an error based on a provided notifier observable.
Example:
    
    ```jsx
    import { of, throwError, timer } from 'rxjs';
    import { retryWhen, mergeMap } from 'rxjs/operators';
    
    const source = of('Initial Value', throwError('Error')).pipe(
      retryWhen(errors => errors.pipe(
        mergeMap((error, index) => {
          if (index < 2) {
            return timer(1000); // Retry after 1 second
          }
          return throwError('Max retry attempts reached');
        })
      ))
    );
    
    source.subscribe(
      result => console.log(result),
      error => console.log('Caught error:', error)
    );
    
    // Output:
    // Initial Value
    // Initial Value
    // Initial Value
    // Caught error: Max retry attempts reached
    ```
    
    Use case: `retryWhen` is useful when you want to dynamically control the retry behavior based on a notifier observable. It allows for more advanced retry strategies, such as delaying retries, limiting the number of retries, or applying custom logic for determining whether to retry or not.
    
4. `onErrorResumeNext`: Ignores errors from the source observable and subscribes to the next observable in the sequence.
Example:
    
    ```jsx
    import { of, throwError } from 'rxjs';
    import { onErrorResumeNext } from 'rxjs/operators';
    
    const source1 = of(1, 2, throwError('Error 1'));
    const source2 = of(3, 4, 5);
    
    source1.pipe(
      onErrorResumeNext(source2)
    ).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 2
    
    // 3
    // 4
    // 5
    ```
    
    Use case: `onErrorResumeNext` is useful when you have multiple observables and want to continue the sequence by subscribing to the next observable even if an error occurs. It allows for graceful error handling and seamless switching between observables.
    
5. `throwError`: Creates an observable that immediately emits an error using a specified error message or error object.
Example:
    
    ```jsx
    import { throwError } from 'rxjs';
    
    throwError('This is an error').subscribe({
      error: error => {
        console.log('Caught error:', error);
      }
    });
    
    // Output:
    // Caught error: This is an error
    
    ```
    
    Use case: `throwError` is used to create an observable that emits an error immediately. It is often used in scenarios where you want to explicitly throw an error within an observable sequence.
    
6. `finalize`: Performs a specified action when the source observable completes, errors, or gets unsubscribed.
Example:
    
    ```jsx
    import { of } from 'rxjs';
    import { finalize } from 'rxjs/operators';
    
    const source = of(1, 2, 3);
    
    source.pipe(
      finalize(() => {
        console.log('Finalize action');
      })
    ).subscribe(result => {
      console.log(result);
    });
    
    // Output:
    // 1
    // 2
    // 3
    // Finalize action
    ```
    
    Use case: `finalize` is useful when you want to perform a specific action when the observable completes, errors, or gets unsubscribed. It allows for cleanup operations, resource releasing, or logging activities to be performed regardless of the observable's outcome.
    

# Advance Concepts in RXJS

1. **Backpressure**: Backpressure is a mechanism for handling situations where the rate of emissions from an observable is faster than the rate at which the observer can consume/process those emissions. It helps prevent overwhelming the consumer with a large number of emitted values.
    - Example: Imagine a real-time data stream producing events faster than the consumer can handle. By applying backpressure mechanisms, such as using buffer operators like `bufferCount` or `bufferTime`, you can control the rate at which the consumer processes the events, preventing overload and ensuring smooth processing.
    - Use case: Handling high-frequency event streams, such as sensor data, network packets, or stock market data, where the consumer may need to process or aggregate events at a manageable pace to avoid overwhelming system resources.

```jsx
import { interval } from 'rxjs';
import { bufferTime } from 'rxjs/operators';

const source = interval(100); // Emits values every 100ms

source.pipe(
  bufferTime(500) // Buffer values for 500ms
).subscribe(bufferedValues => {
  console.log('Buffered Values:', bufferedValues);
});
```

1. **Schedulers**: Schedulers in RxJS provide control over when and where the work associated with an observable is executed. They allow you to define the execution context, such as running the observable's logic on a specific thread, asynchronously, or with a delay. Schedulers help manage concurrency and provide options for fine-grained control over the timing and execution of observables.
    - Example: Using the `observeOn` operator with a scheduler, such as `observeOn(Rx.Scheduler.async)`, you can offload heavy computational or blocking tasks to a separate thread, keeping the main thread responsive and ensuring non-blocking execution.
    - Use case: Performing expensive computations, making network requests, or interacting with I/O-bound operations (e.g., file operations, database queries) asynchronously or on a separate thread to prevent UI freezing or blocking the main event loop.
    
    ```jsx
    import { of, asyncScheduler } from 'rxjs';
    import { observeOn } from 'rxjs/operators';
    
    const source = of(1, 2, 3);
    
    source.pipe(
      observeOn(asyncScheduler) // Execute on async scheduler
    ).subscribe(value => {
      console.log('Value:', value);
    });
    ```
    

1. **Time-based operators**: Time-based operators in RxJS allow you to work with time-related events, such as delaying emissions, setting intervals between emissions, or defining time windows for aggregating values. These operators enable you to perform time-dependent operations, schedule actions, and handle time-related scenarios in reactive programming.
    - Example: The `debounceTime` operator is commonly used in search input fields, where you delay the emission of values until the user pauses typing for a certain duration. This reduces unnecessary intermediate emissions and improves the efficiency of triggering search requests.
    - Use case: Throttling user input events, scheduling periodic updates or notifications, handling time-sensitive operations, or creating time-based animations in graphical user interfaces.
    
    ```jsx
    import { interval } from 'rxjs';
    import { debounceTime } from 'rxjs/operators';
    
    const source = interval(200); // Emits values every 200ms
    
    source.pipe(
      debounceTime(500) // Debounce emissions for 500ms
    ).subscribe(value => {
      console.log('Debounced Value:', value);
    });
    ```
    

1. **Subjects**: Subjects in RxJS are special types of observables that act as both an observer and an observable. They can multicast (or broadcast) values to multiple subscribers, making them suitable for scenarios where you want to distribute values to multiple observers. Subjects maintain an internal list of subscribers and can emit values to all subscribers simultaneously.
    - Example: Imagine a chat application where multiple users can send and receive messages. You can use a subject to represent the chat room, where each new message is emitted by the subject and received by all subscribers (users) simultaneously.
    - Use case: Implementing event bus systems, pub-sub architectures, real-time messaging systems, or any scenario where you need to distribute events or data to multiple subscribers in real-time.
    
    ```jsx
    import { Subject } from 'rxjs';
    
    const subject = new Subject<number>();
    
    subject.subscribe(value => {
      console.log('Subscriber A:', value);
    });
    
    subject.subscribe(value => {
      console.log('Subscriber B:', value);
    });
    
    subject.next(1);
    subject.next(2);
    ```
    

1. **Multicasting**: Multicasting is the process of sharing a single source observable among multiple subscribers, enabling multiple observers to receive the same set of emitted values. Subjects and multicast operators (e.g., `publish`, `share`, `multicast`) are commonly used for implementing multicasting in RxJS.
    - Example: In a real-time dashboard displaying multiple widgets (e.g., stock ticker, weather updates, news feed), you can use multicasting to share a single source of data among multiple widgets, ensuring consistent and synchronized updates for all subscribers.
    - Use case: Building real-time dashboards, collaborative applications, real-time analytics, or any scenario where multiple components or consumers need access to the same set of data or events.
    
    ```jsx
    import { interval } from 'rxjs';
    import { multicast, take } from 'rxjs/operators';
    
    const source = interval(1000).pipe(take(5));
    
    const multicasted = source.pipe(
      multicast(() => new Subject())
    );
    
    multicasted.subscribe(value => {
      console.log('Subscriber A:', value);
    });
    
    multicasted.subscribe(value => {
      console.log('Subscriber B:', value);
    });
    
    multicasted.connect();
    ```
    

1. **Hot vs. Cold observables**: Hot observables are those that start emitting values even before any subscriptions are made, and all subscribers receive the same set of values regardless of when they subscribed. Cold observables, on the other hand, start emitting values only after a subscription is made, and each subscriber receives its own independent sequence of values. Subjects and multicast operators create hot observables, while most other observables are cold by default.
    - Example: A cold observable could be a stream of mouse click events, where each subscription receives its own independent sequence of click events. In contrast, a hot observable could be a live audio stream where all subscribers receive the same set of audio data regardless of when they started listening.
    - Use case: Event broadcasting, live data streams, sensor data feeds, or scenarios where multiple subscribers need to receive the same set of values simultaneously.
    
    ```jsx
    import { interval } from 'rxjs';
    import { take } from 'rxjs/operators';
    
    const coldObservable = interval(1000).pipe(take(5));
    
    coldObservable.subscribe(value => {
      console.log('Subscriber A:', value);
    });
    
    setTimeout(() => {
      coldObservable.subscribe(value => {
        console.log('Subscriber B:', value);
      });
    }, 3000);
    ```
    

# Extra’s

## Pipe

In RxJS, the `pipe` function is a method available on observables and is used to apply multiple operators to the source observable in a declarative and composable manner.

The `pipe` function accepts one or more operator functions as arguments and returns a new observable with the operators applied. It does not mutate the original observable but creates a new observable chain.

The `pipe` function allows you to perform a sequence of transformations, filtering, combining, error handling, or any other operations on an observable in a modular way. It enables you to build complex data flows by chaining operators together, improving code readability and maintainability.

Here's an example of using the `pipe` function to apply multiple operators to an observable:

```jsx
import { of } from 'rxjs';
import { map, filter, take } from 'rxjs/operators';

const source = of(1, 2, 3, 4, 5);

source.pipe(
  map(value => value * 2),       // Transform each value by multiplying by 2
  filter(value => value > 5),    // Filter values greater than 5
  take(2)                        // Take the first 2 values
).subscribe(result => {
  console.log(result);
});

// Output:
// 6
// 8
```

In this example, the `pipe` function is used to chain the `map`, `filter`, and `take` operators together. The source observable `source` undergoes transformation, filtering, and is limited to two values before being subscribed to. The output is the result of the applied operations on the source observable.

By using the `pipe` function, you can apply a series of operators to an observable in a concise and organized manner, facilitating the construction of complex data flows and enabling better code reuse.