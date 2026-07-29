Each *package* within a [[Go Modules|module]] is a collection of source files in the same directory that are compiled together. A *package path* is the module path joined with the sub-directory  containing the package (relative to the module root).

You can only declare **one package for each Go source file**.

This is **invalid**:
```go
package main

func main() {
}

package utils

func Add(a, b int) int {
    return a + b
}
```
#### TL;DR

```
One file → one package declaration.
One directory → one package.
Packages are imported explicitly.
```
# Package main

In Go, the `package main` tells go that this package is an **executable program**.

> Basically tells Go: "I'm building an application **not a library**"

When a package is called `main`, Go expects a special function with the same name:

```go
package main  
  
import "fmt"  
  
func main() {  
	fmt.Println("Hello, world!")  
}
```

This is not because the package name and function name must match. It's because Go has a special rule:
> A runnable program must have a package called `main` and a function called `main`.

### TL;DR

> If the package is `main`, Go looks for a `main()` function because that's the program entry point

| Thing          | Purpose                             |
| -------------- | ----------------------------------- |
| `package main` | Marks the package as executable     |
| `func main()`  | Entry point where execution starts  |
| `package auth` | A library package                   |
| `func Login()` | Just a function inside that package |
