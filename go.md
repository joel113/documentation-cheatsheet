# Go Cheat Sheet

`go init mod example/hello` - Initializes a go mmodule

`go mod tidy` - Add missing an remove unused modules

`go run .` - Compiles and runs the go files in the directory

`go build` - Builds a go application using go modules

## Strings

`fmt.Printf("The result is %v.", result)` - String interpolation with Printf

## Functions

```
package main

import "fmt"

func main() {
	result := div(5, 2)
	fmt.Printf("The result is %v.", result)
}

func div(numerator int, denominator int) int {
	if denominator == 0 {
		return 0
	}
	return numerator / denominator
}
```

### Variadic Input

```
package main

import "fmt"

func main() {
	fmt.Printf("The result of addTo is %v.\n", addTo(3, 2, 1))
	fmt.Println(addTo(3, []int{1, 2, 3, 4, 5}...))
}

func addTo(base int, vals ...int) []int {
	out := make([]int, 0, len(vals))
	for _, v := range vals {
		out = append(out, base+v)
	}
	return out
}
```

### Multiple Return Values

```
package main

import (
	"errors"
	"fmt"
	"os"
)

func main() {
	result, remainder, err := divAndRemainder(5, 2)
	anotherResult, _, _, := divAndRemainder(5, 3)
	divAndRemainder(10, 3)
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}
	fmt.Println(result, remainder)
}

func divAndRemainder(numerator int, denominator int) (int, int, error) {
	if denominator == 0 {
		return 0, 0, errors.New("cannot divide by zero")
	}
	return numerator / denominator, numerator % denominator, nil
}

func divAndRemainderWithNamedReturnValues(numerator int, denominator int) (result int, remainder int,
                                                                  err error) {
    if denominator == 0 {
        err = errors.New("cannot divide by zero")
        return result, remainder, err
    }
    result, remainder = numerator/denominator, numerator%denominator
    return result, remainder, err
}
```

### Blank Returns

Never use them.

```
func divAndRemainder(numerator, denominator int) (result int, remainder int,
                                                              err error) {
    if denominator == 0 {
        err = errors.New("cannot divide by zero")
        return
    }
    result, remainder = numerator/denominator, numerator%denominator
    return
}
```

### Function Types

```
type opFuncType func(int,int) int
```

### Anonymous Functions

```
func main() {
    for i := 0; i < 5; i++ {
        func(j int) {
            fmt.Println("printing", j, "from inside of an anonymous function")
        }(i)
    }
}
```

### Closures

```
package main

import (
	"fmt"
)

type Person struct {
	FirstName string
	LastName  string
	Age       int
}

func main() {
	people := []Person{
		{"Pat", "Patterson", 37},
		{"Tracy", "Bobbert", 23},
		{"Fred", "Fredson", 18},
	}
	
	fmt.Println(people)
	
	// sort by last name
	sort.Slice(people, func(i int, j int) bool {
	    return people[i].LastName < people[j].LastName
	})
	fmt.Println(people)
	
	// sort by age
	sort.Slice(people, func(i int, j int) bool {
	    return people[i].Age < people[j].Age
	})
	fmt.Println(people)
}
```

#### Defer

```
func main() {
    if len(os.Args) < 2 {
        log.Fatal("no file specified")
    }
    f, err := os.Open(os.Args[1])
    if err != nil {
        log.Fatal(err)
    }
    defer f.Close()
    data := make([]byte, 2048)
    for {
        count, err := f.Read(data)
        os.Stdout.Write(data[:count])
        if err != nil {
            if err != io.EOF {
                log.Fatal(err)
            }
            break
        }
    }
}
```

```
func DoSomeInserts(ctx context.Context, db *sql.DB, value1, value2 string)
                  (err error) {
    tx, err := db.BeginTx(ctx, nil)
    if err != nil {
        return err
    }
    defer func() {
        if err == nil {
            err = tx.Commit()
        }
        if err != nil {
            tx.Rollback()
        }
    }()
    _, err = tx.ExecContext(ctx, "INSERT INTO FOO (val) values $1", value1)
    if err != nil {
        return err
    }
    // use tx to do more database inserts here
    return nil
}
```

```
func getFile(name string) (*os.File, func(), error) {
    file, err := os.Open(name)
    if err != nil {
        return nil, nil, err
    }
    return file, func() {
        file.Close()
    }, nil
}

f, closer, err := getFile(os.Args[1])
if err != nil {
    log.Fatal(err)
}
defer closer()
```

#### Call by value

Go is a call by value language.

However as maps and slices are implemented by pointers, they behave differently.

## Pointers

```
var x int32 = 10
var y bool = true
pointerX := &x
pointerY := &y
var pointerZ *string
```

`&` - address operator

`*` - indirection operator

`new` - creates a new pointer

Usually, the new keyword is not used, but the address operator:

```
x := &Foo{}

var y string

z := &y
```

### Mutability of values

If a pointer is passed to a function, the function gets a copy of the value of the pointer.

MIT’s course on Software Construction sums up the reasons why: “[I]mmutable types are safer from bugs, easier to understand, and more ready for change. Mutability makes it harder to understand what your program is doing, and much harder to enforce contracts.”

As the Software Construction course materials go on to explain: “[U]sing mutable objects is just fine if you are using them entirely locally within a method, and with only one reference to the object.” Rather than declare that some variables and parameters are immutable, Go developers use pointers to indicate that a parameter is mutable.

### References

https://research.google/pubs/pub40801/

https://www.forrestthewoods.com/blog/memory-bandwidth-napkin-math/

https://segment.com/blog/allocation-efficiency-in-high-performance-go-services/

https://www.ardanlabs.com/blog/2017/05/language-mechanics-on-stacks-and-pointers.html

http://web.mit.edu/6.031/www/fa20/classes/08-immutability/

## Go Ko

`ko build ./cmd/app` - Builds and pushes a container image
