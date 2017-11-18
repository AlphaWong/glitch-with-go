# Objective
Store the init project example about glitch with go

# package.json
```json
{
  "name": "go-example",
  "version": "0.0.1",
  "description": "Example project showing how to use Go on Gltich",
  "author": "Steve Layton",
  "main": "server.js",
  "scripts": {
    "start": "go build server.go && ./server"
  },
  "engines": {
    "node": "6.10.x"
  },
  "repository": {
    "url": "https://glitch.com/edit/#!/go-example"
  },
  "license": "MIT",
  "keywords": [
    "node",
    "glitch",
    "go"
  ]
}

```

# watch.json
```json
{
  "restart": {
    "include": [
      "^server.go$"
    ]
  },
  "throttle": 100
}

```

# server.go
```go
package main

import (
  "fmt"
  "html"
  "net/http"
)

// https://go-example.glitch.me/
func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hello Go!")
}

// https://go-example.glitch.me/love/Go
func love(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Hi there, I love %s!", html.EscapeString(r.URL.Path[6:]))
}

// https://go-example.glitch.me/hacking
func hacking(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Hacking away on Go on Glitch.")
}

func main() {
    http.HandleFunc("/hacking", hacking)
    http.HandleFunc("/love/", love)
    http.HandleFunc("/", handler)
    http.ListenAndServe(":3000", nil)
}

```

# .env
```
# Environment Config

# store your secrets and config variables in here
# only invited collaborators will be able to see your .env values

# reference these in your code with process.env.SECRET

SECRET=
MADE_WITH=
TMPDIR=

# note: .env is a shell file so there can't be spaces around =

```

# Reference
1. https://glitch.com/edit/#!/go-example?path=server.go
1. https://dev.to/shindakun/see-glitch-go-5j
