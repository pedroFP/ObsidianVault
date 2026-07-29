**Zero value** for each type
```go
var name string   // ""  
var age int       // 0  
var active bool   // false  
var price float64 // 0
```
## Short Variable Declaration Operator (`:=`)
> The compiler infers the type from the value.

The main purpose of using this operator to declare and initialize the local variables inside the functions and to narrowing the scope of the variables.

Example:
```go
name := "Alice"
age := 30
```
Shorthand for:
```go
var name string = "Alice"
var age int = 30
```

**You cannot use `:=` without a value **
```
x :=      // ❌ invalid
```
#### TL;DR
- Use `:=` when you're declaring and initializing immediately.
- Use `var` when you need the variable before you know its value, or when you want the zero value.