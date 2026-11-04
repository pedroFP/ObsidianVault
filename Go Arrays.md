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
## What is a Slice?
A slice is basically a descriptor containing three things:
* **Pointer** -> Points to an element of the underlying array.
* **Length** (`len`) -> Number of elements accessible through the slice.
* **Capacity** (`cap`) -> Number of elements ==🔵available== from the slice's start to end.

# Arrays and Slices
These are different things. Arrays are stored in memory while slices are a reference to the section of an array. If we modify an element in a slice it would also modify it in the array that is referencing.

| Array          | Slice             |
| -------------- | ----------------- |
| `[3]int`       | `[]int`           |
| Size specified | No size specified |
| Fixed length   | Dynamic length    |
```go
// Array (fixed size)
arr := [3]int{1, 2, 3}

// Slice (dynamic size)
slice := []int{1, 2, 3}
```

Example 1: A slice created from an array
```go
arr := [5]int{10, 20, 30, 40, 50}

s := arr[1:4]

// Both `arr` and `s` share the same storage
```

Example 2: Slice created directly
```go
s := []int{10, 20, 30}
```
## Does Slices always reference an Array?
Yes. In Go, every non-nil slice is backed by an **underlying array**. Even though you didn't explicitly create an array, Go creates an underlying array automatically.

## Why having slice and array?
Go separates arrays and slices because they separate two different problems:
* **Arrays** provide fixed-size storage with value semantics
* **Slices** provide flexible access to that storage ==🔵without copying all the elements==
The main reasons are performance, memory efficiency and predictable behavior.
### 1. Arrays are copied when passed around
In Go, arrays are values, just like integers and structs.
```go
func modify(arr [3]int) {
    arr[0] = 99
}

func main() {
    arr := [3]int{1, 2, 3}

    modify(arr)

    fmt.Println(arr) // [1 2 3]
}
```
The function receives a copy of an entire array!
Imagine passing an array containing one million integers. Copying would be expensive.
### 2. Slices avoid copying the entire array
```go
func modify(s []int) {
    s[0] = 99
}

func main() {
    s := []int{1, 2, 3}

    modify(s)

    fmt.Println(s) // [99 2 3]
}
```
Instead of copying the elements, Go copies only the small descriptor (pointer, length and capacity)
![640](data:image/svg+xml;charset=utf-8,%3Csvg%20font-family%3D%22-apple-system-body%2C%20ui-sans-serif%2C%20-apple-system%2C%20system-ui%2C%20Segoe%20UI%2C%20Helvetica%2C%20Apple%20Color%20Emoji%2C%20Arial%2C%20sans-serif%2C%20Segoe%20UI%20Emoji%2C%20Segoe%20UI%20Symbol%22%20font-weight%3D%22400%22%20data-d-component%3D%22svg%22%20fill%3D%22currentColor%22%20style%3D%22color%3Argb\(237%2C%20237%2C%20237\)%22%20viewBox%3D%220%200%20330%20168%22%20width%3D%22100%25%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Crect%20x%3D%228%22%20y%3D%2212%22%20width%3D%22112%22%20height%3D%22112%22%20rx%3D%227%22%20fill%3D%22%2364748b%22%20fill-opacity%3D%22.09%22%20stroke%3D%22%2364748b%22%2F%3E%3Ctext%20x%3D%2264%22%20y%3D%2230%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%20fill%3D%22currentColor%22%3ESlice%3C%2Ftext%3E%3Crect%20x%3D%2217%22%20y%3D%2239%22%20width%3D%2294%22%20height%3D%2223%22%20rx%3D%223%22%20fill%3D%22%2364748b%22%20fill-opacity%3D%22.12%22%2F%3E%3Ctext%20x%3D%2264%22%20y%3D%2255%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22currentColor%22%3EPointer%3C%2Ftext%3E%3Crect%20x%3D%2217%22%20y%3D%2265%22%20width%3D%2294%22%20height%3D%2223%22%20rx%3D%223%22%20fill%3D%22%2364748b%22%20fill-opacity%3D%22.12%22%2F%3E%3Ctext%20x%3D%2264%22%20y%3D%2281%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22currentColor%22%3ELength%3A%203%3C%2Ftext%3E%3Crect%20x%3D%2217%22%20y%3D%2291%22%20width%3D%2294%22%20height%3D%2223%22%20rx%3D%223%22%20fill%3D%22%2364748b%22%20fill-opacity%3D%22.12%22%2F%3E%3Ctext%20x%3D%2264%22%20y%3D%22107%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22currentColor%22%3ECapacity%3A%203%3C%2Ftext%3E%3Cpath%20d%3D%22M111%2050%20H155%20V82%20H181%22%20fill%3D%22none%22%20stroke%3D%22%230D9488%22%20stroke-width%3D%222%22%2F%3E%3Cpath%20d%3D%22M175%2077%20L182%2082%20L175%2087%22%20fill%3D%22none%22%20stroke%3D%22%230D9488%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20x%3D%22254%22%20y%3D%2239%22%20font-size%3D%2212%22%20font-weight%3D%22600%22%20text-anchor%3D%22middle%22%20fill%3D%22currentColor%22%3EUnderlying%20array%3C%2Ftext%3E%3Crect%20x%3D%22184%22%20y%3D%2266%22%20width%3D%2244%22%20height%3D%2233%22%20rx%3D%223%22%20fill%3D%22%230D9488%22%20fill-opacity%3D%22.15%22%20stroke%3D%22%230D9488%22%2F%3E%3Ctext%20x%3D%22206%22%20y%3D%2287%22%20text-anchor%3D%22middle%22%20font-size%3D%2212%22%20fill%3D%22currentColor%22%3E10%3C%2Ftext%3E%3Crect%20x%3D%22230%22%20y%3D%2266%22%20width%3D%2244%22%20height%3D%2233%22%20rx%3D%223%22%20fill%3D%22%230D9488%22%20fill-opacity%3D%22.15%22%20stroke%3D%22%230D9488%22%2F%3E%3Ctext%20x%3D%22252%22%20y%3D%2287%22%20text-anchor%3D%22middle%22%20font-size%3D%2212%22%20fill%3D%22currentColor%22%3E20%3C%2Ftext%3E%3Crect%20x%3D%22276%22%20y%3D%2266%22%20width%3D%2244%22%20height%3D%2233%22%20rx%3D%223%22%20fill%3D%22%230D9488%22%20fill-opacity%3D%22.15%22%20stroke%3D%22%230D9488%22%2F%3E%3Ctext%20x%3D%22298%22%20y%3D%2287%22%20text-anchor%3D%22middle%22%20font-size%3D%2212%22%20fill%3D%22currentColor%22%3E30%3C%2Ftext%3E%3Ctext%20x%3D%22254%22%20y%3D%22121%22%20text-anchor%3D%22middle%22%20font-size%3D%2210%22%20fill%3D%22currentColor%22%3EActual%20element%20storage%3C%2Ftext%3E%3Ctext%20x%3D%22165%22%20y%3D%22151%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22%230D9488%22%3ECopy%20descriptor%2C%20not%20elements%3C%2Ftext%3E%3C%2Fsvg%3E)
This makes passing large collections around much cheaper.
### 3. Slices allow dynamic growth
An array as fixed length:
```go
arr := [3]int{1, 2, 3}
```
You cannot append a fourth element to this array.

A slice can grow 
```go
s := []int{1, 2, 3}
s = append(s, 4)
s = append(s, 5)
```
### 4. Slices allow working with parts of arrays
Suppose you have 1,000 elements but want to process only 100:
```go
arr := [1000]int{}

s := arr[100:200]
```
No elements are copied. The slice simply references that portion of the array.

This is particularly useful for processing buffers, files, network packets and large datasets