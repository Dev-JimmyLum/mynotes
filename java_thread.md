## Linear Process -- Read DB

- Slow

```java
Object money = userservice.getMoneyData();

Object user = userservice.getUserData();
```

## MultiThreading -- Read DB

- If high request will consume pressure back-end server

```java
Callable ?
Thread ?
```

## Scheduler Thread Pool

- CompletedFutureTask

- Assign serial no each of the request.

- Trigger the reading every 10ms 

```java
SchedulerThreadPoolExector
FutureTask
Completeable-Future.
```
