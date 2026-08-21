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

### Functions
- `supplyAsync()`: Running asynchronous tasks than return values. Turns the output as a `CompletableFuture<T>` than we can do chained actives on. 
```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureSupplyAsync {
    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Hello, Async!";
        });

        System.out.println(future.join()); // Hello, Async!
    }
}

```

- `runAsync()`: like `supplyAsync()` but for the tasks that don't return a value. This code executes a task asynchronously using `CompletableFuture`. The task runs independently, and after its completion, control returns to the main program. The program ensures the task is completed and then displays a task completion message.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureRunAsync {
    public static void main(String[] args) {
        CompletableFuture<Void> future = CompletableFuture.runAsync(() -> {
            try {
                Thread.sleep(1500);
                System.out.println("Running a task asynchronously!");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        });

        future.join(); // Waits for the task to complete
        System.out.println("Task completed!");
    }
}


```
- `thenApply()`: combined tasks. (for chained activity)
```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureChain {
    public static void main(String[] args) {
        CompletableFuture.supplyAsync(() -> "Hello")
            .thenApply(result -> result + ", World!")
            .thenApply(String::toUpperCase)
            .thenAccept(System.out::println); //HELLO, WORLD!
    }
}

```

- `thenRun()`: Taking action after completing task.
Sometimes, after the main task finishes, we need to execute an operation that has no specific input or output. In this case, we use `thenRun()`:

This code executes a task asynchronously using `CompletableFuture`. After the main task completes, another task is automatically executed to complete the processing of the result. The program is designed in such a way that it ensures it does not terminate prematurely until all tasks are completed.
```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureThenRun {
    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Hello, World!";
        });

        future.thenRun(() -> {
            System.out.println("The main task has finished!");
        });

        future.join();
    }
}

```

- `allOf()`: Doing all the tasks. `allOf()` is used when you want all tasks to run concurrently and wait for all of them to complete.

This code executes two asynchronous tasks using `CompletableFuture` and uses the `allOf()` method to wait for all of them to finish. After all tasks are completed, a message indicating that all tasks are done is displayed.
```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureAllOf {
    public static void main(String[] args) {
        CompletableFuture<Void> future1 = CompletableFuture.runAsync(() -> {
            try {
                Thread.sleep(1000);
                System.out.println("Task 1 completed");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        });

        CompletableFuture<Void> future2 = CompletableFuture.runAsync(() -> {
            try {
                Thread.sleep(2000);
                System.out.println("Task 2 completed");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        });

        CompletableFuture<Void> allTasks = CompletableFuture.allOf(future1, future2);
        allTasks.join(); // Waits for all tasks to complete

        System.out.println("All tasks completed");
    }
}

```
- `anyOf()`: Doing one of the tasks. 
If you only want to wait for one of the tasks to complete, use `anyOf()`.

This code executes two asynchronous tasks using `CompletableFuture` and uses the `anyOf()` method to wait for the first task that completes. The result of the first completed task is processed and displayed.
```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureAnyOf {
    public static void main(String[] args) {
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Task 1";
        });

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Task 2";
        });

        CompletableFuture<Object> anyTask = CompletableFuture.anyOf(future1, future2);
        anyTask.thenAccept(result -> System.out.println("First completed task: " + result));  //First completed task: Task 1
    }
}

```

`anyOf()` returns the result of one of the tasks as soon as it completes.

---
[[Java]]