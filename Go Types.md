In Go, `type` and [[Go Structs|struct]] are related, but they do different jobs. Using `type` defines a new named type, while `struct` is one particular kind of type.

```go
type User struct {
    Name string
    Age  int
}
```

### Type can do much more than create structs
You can create types from different primitives
```go
type UserID int
type Email string
type Temperature float64

// Now we can make APIs much more expressive:
func FindUser(id UserID) {
	// ...
}
```

Add methods to your own types
```go
type Celsius float64

func (c Celsius) Fahrenheit() float64 {
    return float64(c)*9/5 + 32
}
```