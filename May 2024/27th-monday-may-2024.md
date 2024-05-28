A `ReplaySubject` is a type of `Subject` in rxjs thats both an observable and an observer. 
Use use a ReplaySubject in scenarios where you want the new subscribers to receive past values emitted by the subject, ensuring that no data is lost event if subscribers join late . However, be mindful of memory usage, especially if the buffer size is large and emits a high volume of data.
