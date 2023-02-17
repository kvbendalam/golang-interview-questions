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
### Using Sort package
```
package main

import (
	"fmt"
	"sort"
)

func main() {
	// Define an unsorted slice of integers
	nums := []int{3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5}

	// Sort the slice in ascending order
	sort.Ints(nums)

	// Print the sorted slice
	fmt.Println(nums)
}
```
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
35. Compiled programming vs Interpreted programming
36. Question 1: Compare the two variables in golang . 
	a = 10
	b = 10
37. Compare these two maps 
	a = []int{1}
	b = []int{1}
38. Compare two maps
	a = map[string]string{"A": "B"}
	b = map[string]string{"A": "B"}
39. Output of the following:
a := []int{5, 7}
b := []int{6, 6}
check := a
copy(a, b)
fmt.Println(a, b, check)

40. a := []int{5, 7}
b := []int{6, 8}
check := a
a = b
fmt.Println(a, b, check)

41. Question: Arrange the key in sorted order:
	fruits := map[string]int{
		"oranges": 100,
		"apples":  200,
		"bananas": 300,
	}
```
package main


import (
	"fmt"
	"sort"
)


func main() {
	values := map[string]int{
		"cherry": 30,
		"apple":  10,
		"banana": 20,
	}


	keys := make([]string, 0, len(values))
	for key := range values {
		keys = append(keys, key)
	}


	sort.Strings(keys)
	fmt.Println(keys)


	for _, key := range keys {
		fmt.Println(key, values[key])
	}
}

```

42. Question: 
Implement WordCount. It should return a map of the counts of each “word” in the string s. 
 
Bonus: The wc. Test function runs a test suite against the provided function and prints success or failure.


PASS
 f("I am learning Go!") = 
  map[string]int{"Go!":1, "I":1, "am":1, "learning":1}
PASS
 f("The quick brown fox jumped over the lazy dog.") = 
  map[string]int{"The":1, "brown":1, "dog.":1, "fox":1, "jumped":1, "lazy":1, "over":1, "quick":1, "the":1}
PASS
 f("I ate a donut. Then I ate another donut.") = 
  map[string]int{"I":2, "Then":1, "a":1, "another":1, "ate":2, "donut.":2}
PASS
 f("A man a plan a canal panama.") = 
  map[string]int{"A":1, "a":2, "canal":1, "man":1, "panama.":1, "plan":1}
  
  
43. Type conversion from string to integers


44. Create a pointer and store and type convert it


45. How to run different applications in same port 


46. How to optimize data base queries


47. How to copy postgres table 


48. How to write unit tests in golang







