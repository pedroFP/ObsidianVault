You can export a [[Create Go Structs & Custom Types|Struct]] and still not export all the fields in that struct.
To make the fields accessible from outside the package we have to start the field name with the first character in uppercase.
```go
// package user/user.go
type User struct {
	firstName string    // not available ❌
	LastName  string    // avaialabe ✔️
	birthDate string    // not available ❌
	createdAt time.Time // not available ❌
}
```