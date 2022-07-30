# Java Cheat Sheet

## JShell

`jshell` - Open the jshell java repl

`/exit` - Exits the jshell java repl

## String Operations

`String message = "Hi, %s".formatted("Johannes")` - Interpolates a string

## Java Streams

```
result = employees.stream().filter(e -> !e.isActive()).count() > 0;
```

```
result = employees.stream().anyMatch(e -> !e.isActive());
```

## Java GC Logging

```
    -XX:+PrintCommandLineFlags -version \
    -XX:+PrintGCDetails  \
    -Xlog:gc*=debug:file=/var/log/gc.log \
```
