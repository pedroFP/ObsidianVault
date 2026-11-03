```go
func main() {
	prices := [4]float64{10.99, 20.0, 45.99, 20.0}
	fmt.Println(a...: prices)
}
```

`[amount of elements in the array]type_of_data{values, inside, the, array}` 

```go
var productNames [4]string

fmt.Println(a...: productNames) // it prints => [   ]
```

```go
var productNames [4]string = [4]string{"A book"}
```

# Slices
```go
func main() {
	prices := [4]float64{10.99, 20.0, 45.99, 20.0}
	fmt.Println(a...: prices)
	
	featuredPrices []float64 := prices[1:3] // 👈 Slice
}
```
You can create a slice from a slice
```go
func main() {
	prices := [4]float64{10.99, 20.0, 45.99, 20.0}
	fmt.Println(a...: prices)
	
	featuredPrices []float64 := prices[1:3] // from the 1st to the 3rd index

	highlightedPrices := featuresPrices[:1] // 👈 Slice from a slice
											// from 0 to the 1st index
	
}
```
