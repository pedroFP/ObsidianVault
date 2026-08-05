> https://go.dev/wiki/GOPATH

The GOPATH variable is used for the following purposes
1. The `go install` command installs binaries to `$GOBIN`, which defaults to `$GOPATH/bin`.
2. The `go get`command caches downloaded modules in `$GOMODCACHE`, which defaults to `$GOPATH/pkg/mod`.
3. The The `go get`command caches downloaded checksum database state in `$GOPATH/pkg/sumdb`.

| Variable                     | Path                |
| ---------------------------- | ------------------- |
| `$GOPATH`                    | `$HOME/go`          |
| `$GOBIN`                     | `$GOPATH/bin`       |
| `$GOMODCACHE`                | `$GOPATH/pkg/mod`   |
| downloaded checksum database | `$GOPATH/pkg/sumdb` |
|                              |                     |
