# Structs


```go
type user struct {
  name      string
  lastName  string
}

func (u user) showDetails() {
  fmt.Println(u.name, u.lastNmae)
}
```
