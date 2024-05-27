Apparently you can spread a struct into a struct like so in rust:

```
fn main() {
    struct User {
	    active: bool,
	    username: String,
	    email: String,
	    sign_in_count: u64
	}

	let user1 = User {
		active: true,
		username: String::from("feezyhendrix"),
		email: String::from("one@example.com"),
		sign_in_count: 1,
	};

    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```


You can also use tuple structs without named named fields.

```
struct Point(i32, i32, i32);
struct HexColor(String, i32, i32, i32);
```


Behavior Subject vs Async Subject in Rxjs

They are both Subjects but a Behavior Subject needs to be initialized with a value.
```
import { BehaviorSubject } from 'rxjs';

// Create a BehaviorSubject with an initial value
const behaviorSubject = new BehaviorSubject<number>(0);

// Subscribe to the BehaviorSubject
behaviorSubject.subscribe(value => console.log('Subscriber 1:', value));

// Emit new values
behaviorSubject.next(1);
behaviorSubject.next(2);

// Subscribe to the BehaviorSubject later
behaviorSubject.subscribe(value => console.log('Subscriber 2:', value));

// Emit another value
behaviorSubject.next(3);

```


Async Subject only emits the last value thus when  it's completed `.complete()` is called;

```
import { AsyncSubject } from 'rxjs';

// Create an AsyncSubject
const asyncSubject = new AsyncSubject<number>();

// Subscribe to the AsyncSubject
asyncSubject.subscribe(value => console.log('Subscriber 1:', value));

// Emit new values
asyncSubject.next(1);
asyncSubject.next(2);

// Subscribe to the AsyncSubject later
asyncSubject.subscribe(value => console.log('Subscriber 2:', value));

// Emit another value and complete
asyncSubject.next(3);
asyncSubject.complete();

```
Apparently you can spread a struct into a struct like so in rust:

```
fn main() {
    struct User {
	    active: bool,
	    username: String,
	    email: String,
	    sign_in_count: u64
	}

	let user1 = User {
		active: true,
		username: String::from("feezyhendrix"),
		email: String::from("one@example.com"),
		sign_in_count: 1,
	};

    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```


You can also use tuple structs without named named fields.

```
struct Point(i32, i32, i32);
struct HexColor(String, i32, i32, i32);
```


Behavior Subject vs Async Subject in Rxjs

They are both Subjects but a Behavior Subject needs to be initialized with a value.
```
import { BehaviorSubject } from 'rxjs';

// Create a BehaviorSubject with an initial value
const behaviorSubject = new BehaviorSubject<number>(0);

// Subscribe to the BehaviorSubject
behaviorSubject.subscribe(value => console.log('Subscriber 1:', value));

// Emit new values
behaviorSubject.next(1);
behaviorSubject.next(2);

// Subscribe to the BehaviorSubject later
behaviorSubject.subscribe(value => console.log('Subscriber 2:', value));

// Emit another value
behaviorSubject.next(3);

```


Async Subject only emits the last value thus when  it's completed `.complete()` is called;

```
import { AsyncSubject } from 'rxjs';

// Create an AsyncSubject
const asyncSubject = new AsyncSubject<number>();

// Subscribe to the AsyncSubject
asyncSubject.subscribe(value => console.log('Subscriber 1:', value));

// Emit new values
asyncSubject.next(1);
asyncSubject.next(2);

// Subscribe to the AsyncSubject later
asyncSubject.subscribe(value => console.log('Subscriber 2:', value));

// Emit another value and complete
asyncSubject.next(3);
asyncSubject.complete();

```



