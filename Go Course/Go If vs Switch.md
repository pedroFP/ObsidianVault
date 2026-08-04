j
```go
for {
	if choice = 1 {
		// Do some logic
		continue	
	} else if{
		// Exit
		break
	}
}
```

Inside the switch block you cannot use `break`, you can use `return`, but it finishes the hole loop
```go
for {
	switch choice {
	1:
		// Do some logic
	default:
		return
	}
}
```