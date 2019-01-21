# ProducerConsumerPattern

The producer/consumer relationship seperates the task of indentifying work to be done from the tasks involved in actually carrying out the work. The producer portion of the application generates data and stores it in a synchronized buffer and consumer portion of the application reads data from the shared buffer.

Class `SynchronizedBuffer` implements interface `Buffer` and handles synchronization. The `put` and `take` operations on the shared buffer are guarded by a `ReentrantLock` to prevent corruption. These operations are also **state dependent**: the `put` operation should proceed only if the buffer is in a *not-full state*; and the `take` operation should proceed only if the buffer is in a *not-empty state*. The `Condition` objects declare two different conditions on which producer and consumer have to wait respectively and are assoicated with the `ReentrantLock` object.

Class `Producer` implements the `Runnable` interface, allowing it to be executed as a task in a seperate thread. Class `Consumer` also implements the `Runnable` interface, allowing the `Consumer` to execute concurrently with the `Producer`.
