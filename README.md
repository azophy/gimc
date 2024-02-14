# GIMC: Go's In-Memory Cache

This is a simple In-memory cache implementation, aimed at readibility & learning. The goals are:
- simple, single-value cache
- support for expiration
- single method for getting & setting value
- thread-safe
- (optional) Thundering Herd-resistant

## How to use

```
// first get the package using `go get github.com/azophy/gimc`
package cache

import (
	"fmt"
	"time"

  "github.com/azophy/gimc"
)

var testCache = Cache[int]{}

func main() {
	_, err := testCache.Fetch(10*time.Second, func() (int, error) { return 3, nil })
	res, err := testCache.Fetch(3*time.Second, func() (int, error) { return 5, nil })

	if err != nil {
		fmt.Printf("value from cache is: %d\n", 3) // shoul be 3
	}
}

```

## Running test

```
$ go test cache*.go
```
