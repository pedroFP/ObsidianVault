# Links 🔗

| Desc                                                          | Link                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------ |
| Oficial Go Wiki                                               | https://go.dev/wiki/                                   |
| Goroutines                                                    | https://www.youtube.com/watch?v=vfrAX26cqtg            |
| Packages and Modules in Go                                    | https://notes.kolkhis.dev/golang/modules_and_packages/ |
| Why the Best Codebases Barely Use Inheritance Anymore?        | https://www.youtube.com/watch?v=pbsTy5V_pxA            |
| Goroutines Are NOT Threads (Here's What They Actually Are) !? | https://www.youtube.com/watch?v=vfrAX26cqtg            |
| Pointers in Spanish                                           | https://siemprelisto.cl/tecnologias/go/05-punteros/    |

![[index.base]]

```go
package main

import "fmt"

type Persona struct {
	Nombre string
	Edad   int
}

func main() {
	// p := &Persona{Nombre: "Ana", Edad: 30}
	//
	// // Go permite acceso directo sin (*p).Nombre
	// fmt.Println(p.Nombre) // "Ana"
	// p.Edad = 31
	// fmt.Println(p.Edad) // 31
	//
	// // Esto tambien funciona pero es innecesario
	// fmt.Println((*p).Nombre) // "Ana"

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
