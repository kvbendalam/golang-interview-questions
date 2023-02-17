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
3. Write a program that takes a string as a input and print in its reverse order
```
package main

import (
    "fmt"
    "strings"
)

func reverseWords(s string) string {
    // Split the string into a slice of words
    words := strings.Fields(s)
    
    // Reverse the order of the words in the slice
    for i, j := 0, len(words)-1; i < j; i, j = i+1, j-1 {
        words[i], words[j] = words[j], words[i]
    }
    
    // Join the words back together into a string
    return strings.Join(words, " ")
}

func main() {
    str := "The quick brown fox jumps over the lazy dog"
    reversed := reverseWords(str)
    fmt.Println(reversed)
}
```
4. Write a program that takes a slice of integers and sorts them in ascending order.

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
21. How to compare two slices in golang?
22. How to compare two structs in golang?
23. How to compare two maps in golang?
24. What is the difference between parallelism and concurrency?
25. What is statically typed languages?
26. What is dynamically typed languages?
27. What is race condition?
28. What is defer in golang?
29. What is panic in golang?
30. What is the use of recover in golang?
31. Type assertion in golang?
32. what is rune in golang?
33. what is pointer in golang?
34. Object oriented principles in golang?
35. 
