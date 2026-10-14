An interface is a type that lists methods without providing their code. You can't create an instance of an interface directly, but you can make a variable of the interface type to store any value that has the needed methods.

```go
type Animal interface {
    Speak() string
}

var a Animal // A variable of the interface type
```

Both `Dog` and `Cat` satisfy the `Animal` interface **automatically**.
```go
type Dog struct{}
type Cat struct{}

func (d Dog) Speak() string {
    return "Woof!"
}

func (c Cat) Speak() string {
    return "Meow!"
}
```

A variable of an interface type can hold values of different types, as long as those types implement the methods required by the interface.
```go
var a Animal

func speak(animal Animal) string {
	animal.Speak()
}

d = Dog{}
c = Cat{}

speak(d) // "Woof!"
speak(c) // "Meow!"
```

**This means:** *Anything that has a method called `Speak()` that returns a `string` can be considered an `Animal`*
# Naming Convention
convention name for interfaces with one method is the name of the method plus `er` suffix
```go
type saver interface {
	Save() error
}
```
# Embedded Interfaces
Go interfaces define a set of method signatures and are themselves types, meaning you can declare variables of an interface type.

Although Go does not support traditional inheritance, interfaces support embedding. An interface can embed other interfaces directly or include their method signatures explicitly.  Both approaches produce the same result.

A single interface can embed multiple interfaces. When an embedded interface's method change, those changes are reflected in the embedding interface.

# The Special "Any Value Allowed" Type
 `interface{}` & `any`: a variable can hold a value of any type.
```go
func printSomething(value interface{}) {
	fmt.Println(value)
}

func printSomething(value any) {
	fmt.Println(value)
}

type any = interface{} // go/src/builtin/builtin.go
```