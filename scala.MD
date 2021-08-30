# Scala Cheat Sheet

## Flatmap

flatmap maps every element of a collection including arrays, sequences and lists and removes the most inner grouping of the collection.

### Flatmap with options

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

### Flatmap with functions

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

### Flatmap with maps

```
scala> val map = Map(1 -> "one", 2 -> "two", 3 -> "three")
map: scala.collection.immutable.Map[Int,java.lang.String] = Map(1 -> one, 2 -> two, 3 -> three)

scala> 1 to map.size flatMap(map.get)
res0: scala.collection.immutable.IndexedSeq[java.lang.String] = Vector(one, two, three)
```

### Flatmap links

https://alvinalexander.com/scala/collection-scala-flatmap-examples-map-flatten/
