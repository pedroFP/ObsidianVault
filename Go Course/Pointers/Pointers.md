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