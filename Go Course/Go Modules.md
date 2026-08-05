> https://go.dev/ref/mod#modules-overview

# A `module` Is a Collection of Go Packages
A `module` is a collection of [[Go Packages|Go Packages]]  that are released, versioned, and distributed together. Modules can be downloaded directly from version control repositories (i.e GitHub) or from module proxy servers.

Modules are how Go manages dependencies.
## Organization
* A module is defined by a `go.mod` file at the root of the project directory. This file defines the module path and lists its dependencies
## Purpose
* Modules provide dependency management and versioning.
* A module declares its dependencies, and *Go's toolchain* can automatically download, manage and version those dependencies 
## Usage
* Modules allow for reproductive builds by locking dependencies to specific versions.
* Modules enable developers to work outisde of the traditional GOPATH by providing versioning and package management
	* **[[GOPATH]]** is a legacy workspace setting that is no longer required for modern Go development using Go Modules.
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

