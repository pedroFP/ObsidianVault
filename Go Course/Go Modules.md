> https://go.dev/ref/mod#modules-overview

Modules are how Go manages dependencies.

A *module* is a collection of [[Go Packages|packages]] that are released, versioned, and distributed together. Modules can be downloaded directly from version control repositories (i.e GitHub) or from module proxy servers.
## Init a module

```bash
$ go mod init example.com/my_module
```

It creates a `go.mod` file

```go
module example.com/my_module

go 1.26.4
```

## Go Build Command
It will create an executable file (`.exe` in windows)  that can run without having Go installed
```
$ go build
```

How to run the file on linux
```
📄️ $ ./my_module
```

