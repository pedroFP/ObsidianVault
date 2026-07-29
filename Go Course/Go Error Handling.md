Conventionally Go treats errors as **ordinary return values**, not exceptions
```ruby
accountBalance, err := getBalanceFromFile()

if err != nil {
	fmt.Println("ERROR")
	fmt.Println(err)
	fmt.Println("-----")
}
```

Error is just a type of **value** like an int, float64, etc
```go
import "errors"

func getBalanceFromFile() (float64, error) {
	data, err := os.ReadFile(accountBalanceFile)

	if err != nil {
		return 1000, errors.New("Failed to read file") 
		// 1000 is just an arbitrary number 
	}
}
```

# Panic
> Tool for handling runtime errors

When panic is executed the normal flow of execution is interrupted and the program begins unwinding the call stack, executing deferred function along the way

```go
panic("Some error")
```