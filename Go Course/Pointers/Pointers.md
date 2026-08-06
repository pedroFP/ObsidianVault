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
Avoid Unnecessary Value Copies
Directly Mutate Values