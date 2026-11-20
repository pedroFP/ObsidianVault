  [source 🔗](https://www.zetcode.com/golang/builtins-make/)
  The `make` function allocates and initializes objects of type `slice`, `map` or `channel` returning an initialized value ready to use.
  In Go, `make` is essential for creating complex data structures with specific initial capacities. It ensures proper initialization of internal state.
# Creating a Slice with make
```go
list := make([]int, 2, 2)
fmt.Println(list)

list[0] = 2
list[1] = 1

fmt.Println(list)

// Exceed capacity
list = append(list, 2)
fmt.Println(list)
```
Capacity determines when the underlying array needs reallocation. Appending beyond capacity causes automatic resizing.
# Creating a Maps with make

```go
list := make(map[string]int, 10)

list["foo"] = 2
list["doo"] = 1

fmt.Println(list)

delete(list, "foo")

fmt.Println(list)
```
The capacity hint helps optimize map performance by reducing **rehashing**. Maps dynamically grow regardless of initial capacity. Elements can be added, checked and deleted.