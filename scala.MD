# Scala Cheat Sheet

## Main function

```
object Main {
	def main(args: Array[String]): Unit = {
		// do here something
	}
}
```

## Map

`"10,20,30,60,50".split(",").map(_.toInt).sorted` - Splits, maps and sorts

## Lambda Function

`(value: String) => println(value)`

## Pattern Matching

### Matching a List

#### List Extractors

```
scala> val match_lambda = (list: List[Int]) => list match {
     |      case List() => s"Found an empty list!"
     |      case List(1) => s"Found a list with a 1!"
     |      case List(1,2) => s"Found a list with a 1 and a 2!"
     |      case List(1,2,3) => s"Found a list with a 1, 2 and a 3!"
     |      case _ => s"Found something else!"
     |      }

scala> val list = List(1,2,3)
val list: List[Int] = List(1, 2, 3)

scala> match_lambda(list)
val res0: String = Found a list with a 1, 2 and a 3!
```

#### Haskell Tyle

```
scala> list match {
     | case 1 :: other => "This list is starting with a 1"
     | case _ => "Everything else!"
     | }
val res3: String = This list is starting with a 1
```

#### List Vararg Pattern

```
scala> list match {
     | case List(_, 2, _*) => "This list has a 2 on the second position!"
     | case _ => "Everything else!"
     | }
val res4: String = This list has a 2 on the second position!
```

#### List Infix Pattern

```
scala> val list = List(1,2)
val list: List[Int] = List(1, 2)

scala> list match {
     | case List(1) :+ 2 => "This list is starting with a 1"
     | case _ => "Everything else!"
     | }
val res7: String = This list is starting with a 1
```

### Pattern Matching Links

https://dzone.com/articles/8-scala-pattern-matching-tricks

## Iterating

### For Loops

```
val nums = Seq(1,2,3)
for (n <- nums) println(n)
```

### Foreach Method

```
val people = Seq("Johannes","Alexander","Johanna", "Alexandra")
people.foreach(println)
```

### For and Foreach Decomposition

```
val movieLength = Map(
	"Movie A" -> 123,
	"Movie B" -> 256,
	"Movie C" -> 33
)

for((name, length) <- movieLength) println(s"Movie $name takes $length minutes.")

movieLength.foreach {
	case(name, length) => println(s"Movie $name takes $length minutes.")
}

```

## Mapping and Transforming

### flatmap

flatmap maps every element of a collection including arrays, sequences and lists and removes the most inner grouping of the collection.

#### flatmap with options

```
scala> val strings = Seq("1", "2", "foo", "3", "bar")
strings: Seq[java.lang.String] = List(1, 2, foo, 3, bar)

scala> strings.map(toInt)
res0: Seq[Option[Int]] = List(Some(1), Some(2), None, Some(3), None)

scala> strings.flatMap(toInt)
res1: Seq[Int] = List(1, 2, 3)

scala> strings.flatMap(toInt).sum
res2: Int = 6
```

#### flatmap with functions

```
scala> val list = List(1,2,3,4,5)
list: List[Int] = List(1, 2, 3, 4, 5)

scala> def g(v:Int) = List(v-1, v, v+1)
g: (v: Int)List[Int]

scala> list.map(x => g(x))
res0: List[List[Int]] = List(List(0, 1, 2), List(1, 2, 3), List(2, 3, 4), List(3, 4, 5), List(4, 5, 6))

scala> list.flatMap(x => g(x))
res1: List[Int] = List(0, 1, 2, 1, 2, 3, 2, 3, 4, 3, 4, 5, 4, 5, 6)
```

#### flatmap with maps

```
scala> val map = Map(1 -> "one", 2 -> "two", 3 -> "three")
map: scala.collection.immutable.Map[Int,java.lang.String] = Map(1 -> one, 2 -> two, 3 -> three)

scala> 1 to map.size flatMap(map.get)
res0: scala.collection.immutable.IndexedSeq[java.lang.String] = Vector(one, two, three)
```

#### flatmap links

https://alvinalexander.com/scala/collection-scala-flatmap-examples-map-flatten/

### fold

#### foldLeft

Iterates a list from left to right, passes the element and an accumulator to some function while the result is passed as accumulator to the next iteration.

```
scala> val inputList: List[Int] = List(1, 3, 5)
val inputList: List[Int] = List(1, 3, 5)

scala> inputList.foldLeft(0) { (acc,i) => acc + i}
val res0: Int = 9

scala> inputList.foldLeft(Seq[Int]()) { (acc,i) => acc :+ i}
val res12: Seq[Int] = List(1, 3, 5)
```

Folding can also be used to calculate the length, the last or the average. It can be used to reverse or to operate on options.

#### fold links

https://commitlogs.com/2016/09/10/scala-fold-foldleft-and-foldright/

## Lists

`val result = Option(listMaybeEmpty).filter(_.nonEmpty).map(List("bla"))` - Returns a List with a default string if the other list is empty 

## Futures

A `future` is placeholder object for a value that may not yet exists. By default, future and promises are non-blocking, making use of callbacks instead of typical blocking operations. Future and promises reolve around `ExecutionContext`, which are responsible for execution computations. An `ExecutionContext` is free to execute computations in a new thread, in a pooled thread or in the current thread. By default, the `ExecutionContext.global` sets the parallelism level of its underlying fork-join pool to the number of available processors. The `ForkJoinPool` can increase the number of threads beyonds its `paralelismLevel` in the precense of a blocking operation.

Using Futures means, that an operation independent whether it is blocking or non-blocking is executed on a new thread. In a JVM, it is a Java Thread which is still heavy weight. Hence, it is essential to employ asynchronous communication and avoid blocking in general to utilize the threads as best as possible even if the execution of futures is delegated to a seperate execution context. It is even considered harmful to perform waits on Futures as this also results in a blocking operation. Instead, Callbacks or combinators should be used.


```
ìmplicit val ec: ExecutionContext = ...
val inverseFuture: Future[Matrix] = Future {
	fatMatrix.inverse()
}
```

### Futures Links

https://docs.scala-lang.org/overviews/core/futures.html
https://blog.colinbreck.com/calling-blocking-code-there-is-no-free-lunch/

## Fibers

### Fibers Links

https://blog.softwaremill.com/will-project-loom-obliterate-java-futures-fb1a28508232
https://typelevel.org/blog/2021/02/21/fibers-fast-mkay.html
