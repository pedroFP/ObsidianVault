https://siemprelisto.cl/tecnologias/go/10-metodos/

> Not the same as [[Go Functions]]
 
 In Go a method is a function attached to a `struct`. Methods have a `receiver` in between `func` and the name:

```go
type Rectangle struct {
	Width, Height float64
}

func (r Rectangle) Area() float64 {
	return (r.Width * r.Height)
}

func main() {
	rect := Rectangle{Width: 10, Height: 5}
	fmt.Println(rect.Area()) // 50
}
```

The receiver `(r Rectangle)` tells Go that the `Area` **belongs** to the type `Rectangle`
# Receivers
A `receiver` is what lets you attach a method to a type. There are two important kind:
+ Value receivers
+ Pointer receivers

## Value Receivers
Works on a **copy** of the value. Does not modify the original

```go
type Counter struct {
	Value int
}

func (c Counter) Increment {
	c.Value++ // Modifies the copy, not the original one
}

func main() {
	c := Counter{Value: 0}
	c.Increment()
	fmt.Println(c.Value) // 0 (no changes)
}
```
## Pointer Receivers
Works on the **original** through a pointer

```go
func (c *Counter) Increment() {
	c.Value++ // Modifies the original one
}

func main() {
c := Counter{Value: 0}
	c.Increment()
	fmt.Println(c.Value) // 1
}
```
---
## TL;DR

| Aspect                | Value Receiver `(r T)`            | Pointer Receiver `(r *T)`    |
| --------------------- | --------------------------------- | ---------------------------- |
| Modifies the original | No                                | Yes                          |
| Copies the value      | Yes                               | No (sends pointer)           |
| Concurrent security   | More secured (isolated copy)      | Requires syncing             |
| Big Structs           | Expensive (makes a complete copy) | Efficient (only the pointer) |
| Interfaces            | Satisfies value and pointer       | Only satisfies the pointer   |
# Automatic Resolution of [[Pointers#Operators `&` and `*` 👈|`&` and `*`]]
Go resolves automatically pointers when calling the methods

>`c.Foo(2) == (&c).Foo(2)`
 
```go
type Circle struct {
	Radio float64
}

func (c *Circle) Scale(factor float64) {
	c.Radio *= factor
}

func main() {
	c := Circle{Radio: 5}
	
	// Go converts automatically c into &c
	c.Scale(2) // aquivalent to (&c).Scale(2)
	
	r := &Circle{Radio: 5}
	// Go dereference automatically for value receivers
	r.Radio // aquivalent to (*r).Radio
}
```

