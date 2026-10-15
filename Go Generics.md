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
![[Pasted image 20261014212227.png]]