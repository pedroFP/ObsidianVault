Generics are a feature that enables **parametric polymorphism**.

With generics, you can declare and use functions or types that are written to work with any of a set of types provided by calling code.
## What They Solve?
The problem they solve is about writing reusable and type-safe code without duplicating the same logic for different types.

Imagine you want a function that returns the first element of a slice.
Without generics:
```go
func FirstInt(items []int) int {
    return items[0]
}

func FirstString(items []string) string {
    return items[0]
}

func FirstFloat(items []float64) float64 {
    return items[0]
}
```
All three functions do exactly the same thing, the only difference is the type.
This is **code duplication caused by types**, not by different behavior.

With generics:
```go
func First[T any](items []T) T {
    return items[0]
}
```

`T` is a **type parameter**. It could be thought of it as a variable, but for types rather than values.
![[Pasted image 20261014212227.png]]

When you call `First([]string{"a", "b"})` => Go infers `T = string`
#### Why does everybody use `T`?
Because it's a convention, not a Go keyword.
# List Predefined Types
Here we are saying the `items` can be either `int`, `string` or `float64`.
```go
func First[T int|string|float64](items []T) T {
    return items[0]
}
```