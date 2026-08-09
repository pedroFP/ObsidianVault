# What are "Pointers"?
Variables that store value "addresses" instead of values

| Code        | Computer Memory  |
| ----------- | ---------------- |
| `age := 32` | `0xc00000018050` |
`agePointer := &age` => `0xc00000018050`

```go
age := 32 // 32 is stored IN 0xc00000018050
agePointer := &age // => 0xc00000018050
```
# Why "Pointers"?
* Avoid Unnecessary Value Copies (*not actually a real reason why we use pointers*)
	* By default, Go creates a copy when passing values to functions
* Directly Mutate Values
	* Pass a pointer (address) instead of a value to a function
	* The function can then directly edit the the underlying value - **no return value is required**
	* Can lead to less code (but also to less understandable code or unexpected behaviors)

```go
package main

import "fmt"

type Persona struct {
	Nombre string
	Edad   int
}

func main() {
	person := Persona{Nombre: "Pedro", Edad: 30}

	fmt.Println(person.Nombre)

	person2 := Persona{Nombre: "Érica", Edad: 25}
	fmt.Println(person2.Nombre)

	p := &Persona{Nombre: "asd", Edad: 20}
	fmt.Println(p.Nombre)

	p2 := new(Persona{Nombre: "Using new", Edad: 20})
	fmt.Println(p2.Nombre)
}
```