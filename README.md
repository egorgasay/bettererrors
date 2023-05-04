# bettererrors - package for better error messages [![PkgGoDev](https://pkg.go.dev/badge/golang.org/x/mod)](https://pkg.go.dev/golang.org/x/mod)

# Installation
```bash
go get github.com/egorgasay/bettererrors
```

### 3 levels of error
```go
const Storage string = "storage"
const Logic string = "business logic"
const Handler string = "handler"
```

### 3 JSON variants
```go
JSON() []byte
JSONIdent(prefix, ident string) []byte
JSONPretty() []byte
```

### Example
```go
e, err := storage.GetEvent()
if err != nil {
  fmt.Println(bettererror.New(err).SetAppLayer(bettererror.Storage).JSONPretty())
}
```

### Output
```json
{
    "measure": "2023-05-04T07:34:51.416756501-04:00",
    "layer": "storage",
    "err": "event not found"
}
```
