State the return type of a function. So after the first parenthesis (arguments) we must define the return types

```go
func simpleFunction() string {
	return "some string"
}

func calculateFutureValue(foo, flag float64) (float64, float64) {
	return foo, flag
}
```

### Another way to declare variables in a function

Instead of defining the 
```go
func calculateFutureValue() (float64, float64) {
	foo := 2.1
	flag := 3.1
	return foo, flag
}
```

Declare the variable names in the return parenthesis
```go
func calculateFutureValue() (foo float64, flag float64) {
	foo = 2.1
	flag = 3.1
	return foo, flag
}
```