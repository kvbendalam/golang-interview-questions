# Golang Interview Questions & Answers

1. Write a program that prints the Fibonacci sequence up to a given number n.
```
package main

import "fmt"

func fibonacci(n int) int {
	if n <= 1 {
		return n
	}
	return fibonacci(n-1) + fibonacci(n-2)
}

func main() {
	var number = 10
	for i := 0; i < number; i++ {
		fmt.Println(fibonacci(i))
	}

}
```
2. Write a program that takes a string as input and prints the number of words in the string.
```
package main

import "fmt"

func main() {
	str := "The quick brown fox jumps over the lazy dog"
	numWords := 1
	for _, char := range str {
		if char == ' ' {
			numWords++
		}
	}
	fmt.Printf("The number of words in the string is: %d\n", numWords)
}

```
3. Write a program that takes a slice of integers and sorts them in ascending order.

4. Write a program that takes a slice of strings and removes all duplicates.

5. Write a program that reads a file and counts the number of occurrences of each word in the file.

6. Write a program that takes two slices of integers and returns a slice containing the intersection of the two slices.

7. Write a program that takes a string and checks whether it is a palindrome.

8. Write a program that generates a random number between 1 and 100 and asks the user to guess the number.

9. Write a program that takes a slice of integers and calculates the sum and average of the numbers.

10. Write a program that reads a CSV file and outputs the data as a table.

11. What is Go, and why was it created?
12. How does garbage collection work in Go, and what are some advantages and disadvantages of Go's garbage collector?
13. What are channels in Go, and how are they used?
14. How do you handle errors in Go, and what are some best practices for error handling?
15. What is a goroutine in Go, and how does it differ from a thread?
16. Can you explain what closures are in Go, and how they work?
17. What is a pointer in Go, and how are they used?
18. What is the difference between a slice and an array in Go?
19. How do you handle dependencies in Go, and what are some tools that you can use for dependency management?
20. What are some common concurrency patterns in Go, and how are they used?
