An interface is a type that lists methods without providing their code. You can't create an instance of an interface directly, but you can make a variable of the interface type to store any value that has the needed methods.

```go
type Animal interface {
    Speak() string
}

var a Animal // A variable of the interface type
```

Both `Dog` and `Cat` satisfy the `Animal` interface automatically
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

a = Dog{}
fmt.Println(a.Speak()) // Woof!

a = Cat{}
fmt.Println(a.Speak()) // Meow!
```

**This means:** *Anything that has a method called `Speak()` that returns a `string` can be considered an `Animal`*
