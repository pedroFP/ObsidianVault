> In go only functions, variables and constant that start with an uppercase character are available in other packages ❗

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
> A *runnable* program must have a package called `main` and a function called `main`.

### TL;DR

> If the package is `main`, Go looks for a `main()` function because that's the program entry point

| Thing          | Purpose                             |
| -------------- | ----------------------------------- |
| `package main` | Marks the package as executable     |
| `func main()`  | Entry point where execution starts  |
| `package auth` | A library package                   |
| `func Login()` | Just a function inside that package |
# Every Go File Must Be Part Of A Package
That's how different files are then linked together behind the scenes by the compiler

```go
// app.go

package main

func main() {
	presentoptions()
	// ....
}
```

We are adding this function to the `package main`  
```go
// communication.go

package main // 👈 adding functions to package main

import "fmt"

func presentOptions() {
	fmt.Println("options")
}
```

# Exporting a Function

```bash
├── balance.txt
├── bank.go
├── communcation.go
├── fileops
│   └── fileops.go
└── go.mod
```

`go.mod`
```go
module example.com

go 1.26.5
```

`bank.go`
```go
package main

const fileName = "balance.txt"

import (
	"fmt"
	"example.com/fileops"
)

func main() {
	// function imported into the main package
	presentOptions()
	
	// function imported from the fileops package
	accountBalance, err := fileops.GetFloatFromFile(fileName)
}
```

## Into the `main` package
>No need to name the function with uppercase on the first character

`communication.go`
```go
package main

import "fmt"

func presentOptions() {
	// ...
}
```

## Multiple Packages
>In Go, only functions, variables and constants that start with an uppercase character are **available in other packages**

Package needs to be stored under a folder with the same name
```
├── fileops
│   └── fileops.go
```

```go
package fileops

import (
	"errors"
	"fmt"
	"os"
	"strconv"
)

func foo(){ // 👈 Not gonna be exported
	// ...
}

func GetFloatFromFile(fileName string) (float64, error) {
	// ...
}
```