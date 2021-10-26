# go-generate-generated

Repo for testing how Cachito handles packages, specifically for repos which use `go generate`. See [go generate](https://go.dev/blog/generate). <br/>
Such repos can be identified with a `//go:generate ...` comment in the `main.go` file. <br/>
There are **4** of these repos with distinct characteristics: <br/>
1. [Directory foobar is empty and `main.go` does not import package `foobar`](https://github.com/cachito-testing/go-generate) <br/>
2. **Directory foobar contains `foobar.go` and `main.go` does not import package `foobar`** <br/>
3. [Directory foobar is empty and `main.go` imports package `foobar`](https://github.com/cachito-testing/go-generate-imported) <br/>
4. [Directory foobar contains `foobar.go` and `main.go` imports package `foobar`](https://github.com/cachito-testing/go-generate-imported-generated) <br/>

This is **case 2**. In this case, Cachito request recognizes both "main" and "foobar" as packages (2pkg, 0dep) <br/>
├── foobar <br/>
│   └── foobar.go ("package foobar", generated) <br/>
└── main.go ("package main") <br/>
