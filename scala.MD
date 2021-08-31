# Scala Cheat Sheet

## flatmap

flatmap maps every element of a collection including arrays, sequences and lists and removes the most inner grouping of the collection.

### flatmap with options

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

### flatmap with functions

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

### flatmap with maps

```
scala> val map = Map(1 -> "one", 2 -> "two", 3 -> "three")
map: scala.collection.immutable.Map[Int,java.lang.String] = Map(1 -> one, 2 -> two, 3 -> three)

scala> 1 to map.size flatMap(map.get)
res0: scala.collection.immutable.IndexedSeq[java.lang.String] = Vector(one, two, three)
```

### flatmap links

https://alvinalexander.com/scala/collection-scala-flatmap-examples-map-flatten/

## fold

### foldLeft

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

### fold links

https://commitlogs.com/2016/09/10/scala-fold-foldleft-and-foldright/

# Lists

`val result = Option(listMaybeEmpty).filter(_.nonEmpty).map(List("bla"))` - Returns a List with a default string if the other list is empty 
