# Structs
Structs are the main mechanism in Go to group related data. Unlike Object Oriented languages, Go uses composition over inheritance through structs and embedding.

```go
type user struct {
  name      string
  lastName  string
}[[Create Go Structs & Custom Types]]

func (u user) showDetails() {
  fmt.Println(u.name, u.lastNmae)
}
```
## Pointers to Structs
Go allows to access fields of a [[Pointers|pointer]] without explicit de-referencing.

```go
p := &Person{Name: "Charles", Age: 43}

// Go de-references automatically
fmt.Println(p.Nombre) // equals to (*p).Nombre

// Modify through the pointer
p.Age = 41
fmt.Println(p.Age) // 41
```
## Constructor Functions
Go does not have `constructors`, but by convention `New-functions` are used.

```go
type Server struct {
	host    string
	port    string
	timeout time.Duration
}

func NewServer(host string, port string) *Server {
	return &Server{
		host: host,
		port: port,
		timeout: 30 * time.Second,
	}
}

func main() {
	myServer := NewServer("localhost", 8080)
	fmt.Printf("Server in %s:%d", myServer.host, myServer.port)
}
```