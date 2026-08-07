---
title: Threads
publish: true
date created: 2026-08-06
tags:
  - java
  - threads
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

## Executor Framework
In big programs, manually managing the threads might not be a good idea. So we can use this tool to manage Thread Pools.
### Executor
The main interface for the tasks. A task is sent to `execute()` and runs asynchronously. 
### ExecutorService
A subclass of Executor that has more options. Like performing the tasks.
- Creating a `Thread Pool` with `Fixed Thread Pool`. Example:
```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Main {
    public static void main(String[] args) {
        // Create a thread pool with 3 threads
        ExecutorService executor = Executors.newFixedThreadPool(3);

        for (int i = 1; i <= 5; i++) {
            final int taskNumber = i;
            executor.execute(() -> {
                System.out.println("Executing Task " + taskNumber + " on Thread: " + Thread.currentThread().getName());
                try {
                    Thread.sleep(2000); // Simulate task processing
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }
            });
        }

        executor.shutdown(); // Gracefully shuts down the executor
    }
}

```

- Using `submit()` for receiving the result.
- `invokeAll()` for running several tasks at the same time. Example:
```java
import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class Main {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(3);

        List<Callable<String>> tasks = new ArrayList<>();
        for (int i = 1; i <= 5; i++) {
            final int taskNumber = i;
            tasks.add(() -> {
                Thread.sleep(1000); // Simulate task processing
                return "Task " + taskNumber + " completed";
            });
        }

        try {
            List<Future<String>> results = executor.invokeAll(tasks);
            for (Future<String> result : results) {
                System.out.println(result.get());
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            executor.shutdown();
        }
    }
}

```

- `shutdown()`: stops receiving new tasks.
- `shutdownNow()`: Immediately stops the running tasks.
- `awaitTermination()`: Waits until the tasks are done or a certain amount of time is passed. Example:
```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class Main {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(2);

        for (int i = 1; i <= 5; i++) {
            final int taskNumber = i;
            executor.execute(() -> {
                System.out.println("Executing Task " + taskNumber);
                try {
                    Thread.sleep(2000);
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }
            });
        }

        executor.shutdown();
        try {
            if (!executor.awaitTermination(15, TimeUnit.SECONDS)) {
                executor.shutdownNow();
            }
        } catch (InterruptedException e) {
            executor.shutdownNow();
        }

        System.out.println("All tasks finished.");
    }
}

```

## CompletableFuture Class
A tool for managing synchronizing and not synchronizing tasks. It has:
- Non-blocking Execution.
- Task Composition.
- Managing results and error.
- Customized Thread Pool.



---
[[Java]]