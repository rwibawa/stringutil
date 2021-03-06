# stringutil
My first library in golang. [tutorial](https://golang.org/doc/code.html).

## 1. Setup
```bash
$ export GOROOT=<directory of the go command line, e.g. /usr/local/Cellar/go/1.9>
$ export GOPATH=<directory of the go workspace, e.g. ~/Document/workspace_go>
$ export GOBIN=$GOPATH/bin  # go binary directory

$ mkdir $GOPATH/src/github.com/rwibawa/stringutil
$ cd $GOPATH/src/github.com/user/stringutil
$ vi reverse.go
$ go build
$ go install

$ vi .gitignore
$ git init
$ git add -A
$ git commit -m "init repo"
$ git remote add origin git@github.com:rwibawa/stringutil.git
$ git push -u origin master
```

### reverse.go
```go
// Package stringutil contains utility functions for working with strings.
package stringutil

// Reverse returns its argument string reversed rune-wise left to right.
func Reverse(s string) string {
    r := []rune(s)
    for i, j := 0, len(r)-1; i < len(r)/2; i, j = i+1, j-1 {
        r[i], r[j] = r[j], r[i]
    }
    return string(r)
}
```

### directory structure
```
src/
    github.com/rwibawa/
        stringutil/
            reverse.go
        hello/
            hello.go

pkg/
    darwin_amd64/
        github.com/rwibawa/
            stringutil.a
```

## 2. Use the library
### Get the stringutil library
```bash
$ go get github.com/rwibawa/stringutil
$ go build github.com/rwibawa/stringutil

$ mkdir $GOPATH/src/github.com/rwibawa/hello
$ vi hello.go
$ go build hello.go
$ ./hello
```

### hello.go
```go
package main

import (
    "fmt"
    "github.com/rwibawa/stringutil"
)

func main() {
    fmt.Printf(stringutil.Reverse("!oG ,olleH"))
}
```
