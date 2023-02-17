# Golang Interview Questions & Answers

1. Write a program that prints the Fibonacci sequence up to a given number n.
```
// You can edit this code!
// Click here and start typing.
package main

import "fmt"

type Person struct {
	name string
}

type Printer interface {
	print()
}

func (p Person) print() {
	fmt.Println(p.name)
}

func main() {
	var p Printer
	p = Person{"Vamsi"}
	p.print()
}

```
