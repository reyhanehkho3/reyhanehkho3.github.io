---
title: Threads
publish: true
date created: 2026-08-06
---
Threads are a unit of running inside a process. A java program usually has a Main Thread used for running the code. We can have threads via `Thread` or `Runnable` interface.
- Example:
```java
public class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread is running...");
    }

    public static void main(String[] args) {
        MyThread thread = new MyThread(); // Creating a thread
        thread.start(); // Starting the thread
    }
}

```

Using the interface is more recommended.
## Thread class
- `start()`: makes a new thread and runs the `run()` method.
- `sleep(long millis)`: the thread goes to sleep for a while.
- `join()`: the current thread waits until the other thread is is done.
- `isAlive()` : checks if the thread is alive.
A good example:
```java
public class JoinExample {
    public static void main(String[] args) {
        Thread thread1 = new Thread(() -> {
            try {
                Thread.sleep(2000); // Simulate work
                System.out.println("Thread 1 finished.");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        });

        Thread thread2 = new Thread(() -> {
            System.out.println("Thread 2 finished.");
        });

        thread1.start();
        thread2.start();

        try {
            thread1.join(); // Waits for thread1 to finish
            thread2.join(); // Waits for thread2 to finish
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }

        System.out.println("All threads finished.");
    }
}

```

### Synchronizing the threads
The key word `synchronized` is used to make sure only one thread can access a certain part of the code at the time.

This is an example of using synchronization for solving Race Conditions. 