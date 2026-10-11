> ▶ [Course link](https://asi.udemy.com/course/go-the-complete-guide/learn/lecture/40838208#overview)

This way only reads one character
```go
var value string
fmt.Scanln(&value)
```

This way we read the hole input till the line scape (`\n`)
```go
reader := bufio.NewReader(os.Stdin)
reader.ReadString('\n')
```
