# GIMC: Go's In-Memory Cache

A Go package for in-memory caching. Aiming at thread-safety, simplicity & code readability.
- simple, single-value cache
- support for expiration
- single method for getting & setting value
- thread-safe
- (optional) Thundering Herd-resistant

## How to use

```go
// first get the package using `go get github.com/azophy/gimc`
package main

import (
  "fmt"
  "time"

  "github.com/azophy/gimc"
)

var testCache = cache.Cache[int]{}

func main() {
  _, err := testCache.Fetch(10*time.Second, func() (int, error) { return 3, nil })
  res, err := testCache.Fetch(3*time.Second, func() (int, error) { return 5, nil })

  if err != nil {
    fmt.Println(err.Error())
  }

  fmt.Printf("value from cache is: %d\n", res)
}

```

## Running test

```
$ go test cache*.go
```
