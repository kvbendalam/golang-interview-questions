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

### Without using sort package
```
package main

import "fmt"

func BubbleSort(array[] int)[]int {
   for i:=0; i< len(array)-1; i++ {
      for j:=0; j < len(array)-i-1; j++ {
         if (array[j] > array[j+1]) {
            array[j], array[j+1] = array[j+1], array[j]
         }
      }
   }
   return array
}

func main() {
   array:= []int{11, 14, 3, 8, 18, 17, 43};
   fmt.Println(BubbleSort(array))
}

```
4. Write a program that takes a slice of strings and removes all duplicates.
```
package main

import "fmt"

func removeDuplicates(strs []string) []string {
	// Create a map to keep track of which elements have been seen before
	seen := make(map[string]bool)

	// Create a new slice to hold the unique elements
	uniqueStrs := []string{}

	// Iterate over the input slice
	for _, str := range strs {
		// If we haven't seen this element before, add it to the new slice
		if !seen[str] {
			seen[str] = true
			uniqueStrs = append(uniqueStrs, str)
		}
	}

	// Return the new slice with duplicates removed
	return uniqueStrs
}

func main() {
	// Define a slice of strings with duplicates
	strs := []string{"apple", "banana", "cherry", "apple", "banana"}

	// Remove duplicates from the slice
	uniqueStrs := removeDuplicates(strs)

	// Print the result
	fmt.Println(uniqueStrs)
}
```
5. Write a program that takes two slices of integers and returns a slice containing the intersection of the two slices.
```
package main

import "fmt"

func intersection(a, b []int) []int {
    // Create a map to store the elements of the first slice
    m := make(map[int]bool)
    for _, x := range a {
        m[x] = true
    }

    // Iterate over the elements of the second slice and add to result if in map
    var res []int
    for _, x := range b {
        if m[x] {
            res = append(res, x)
        }
    }

    return res
}

func main() {
    // Define two slices of integers
    a := []int{1, 2, 3, 4, 5}
    b := []int{3, 4, 5, 6, 7}

    // Find the intersection of the two slices
    c := intersection(a, b)

    // Print the intersection
    fmt.Println(c)
}

```

6. Write a program that takes a string and checks whether it is a palindrome.
```
package main

import "fmt"

func isPalindrome(s string) bool {
    // Convert the string to a slice of runes for efficient processing
    r := []rune(s)

    // Iterate over the characters, comparing those at opposite ends
    for i := 0; i < len(r)/2; i++ {
        if r[i] != r[len(r)-i-1] {
            return false
        }
    }

    return true
}

func main() {
    // Test the isPalindrome function with some examples
    fmt.Println(isPalindrome("racecar"))  // true
    fmt.Println(isPalindrome("hello"))    // false
    fmt.Println(isPalindrome("level"))    // true
    fmt.Println(isPalindrome("rotator"))  // true
}

```

7. Write a program that takes a slice of integers and calculates the sum and average of the numbers.
```
package main

import "fmt"

func calculateSumAndAverage(numbers []int) (int, float64) {
    sum := 0
    for _, num := range numbers {
        sum += num
    }
    average := float64(sum) / float64(len(numbers))
    return sum, average
}

func main() {
    numbers := []int{1, 2, 3, 4, 5}
    sum, average := calculateSumAndAverage(numbers)
    fmt.Printf("Sum: %d, Average: %.2f", sum, average)
}

```
9. What is Go, and why was it created?

	Go, also known as Golang, is an open-source programming language developed by Google. It was first publicly announced in November 2009, and the first stable version, Go 1.0, was released in March 2012.

	Go was created to address some of the shortcomings of existing programming languages, such as C and C++, by providing a more modern and efficient language that can handle large-scale software development projects. The language was designed with the following goals in mind:

	Simplicity: Go is designed to be simple and easy to learn, with a minimalistic syntax and a concise set of features that allow developers to write efficient and readable code.

	Performance: Go is designed to be fast and efficient, with built-in support for concurrency and garbage collection that make it well-suited for modern software development.

	Safety: Go includes features that make it easy to write safe and secure code, including strong typing, memory safety, and garbage collection.

	Openness: Go is an open-source language, with a vibrant community of developers and contributors who are constantly working to improve the language and its ecosystem.

	Overall, Go was created to provide a modern and efficient language that can handle the challenges of large-scale software development, while still being simple and easy to learn. Its popularity has grown rapidly in recent years, with many companies and developers using it for a wide range of applications, including web development, systems programming, and machine learning.

12. How does garbage collection work in Go, and what are some advantages and disadvantages of Go's garbage collector?

	Garbage collection in Go is a process by which the Go runtime manages memory allocation and deallocation for programs written in Go. The garbage collector runs automatically in the background, freeing up memory that is no longer being used by the program.

	The garbage collector in Go uses a mark-and-sweep algorithm, which works by first marking all of the objects that are still being used by the program. It then sweeps through the memory and deallocates any objects that were not marked. This process is repeated periodically to ensure that memory usage is kept under control.

	One advantage of Go's garbage collector is that it allows programmers to focus on writing code without having to worry about memory management. This can make it easier to write correct and reliable code, since it eliminates many of the potential bugs that can arise from manual memory management.

	Another advantage is that the garbage collector is optimized for low-latency, which means that it can perform garbage collection in a way that minimizes disruptions to the program's execution. This can be important for certain types of applications that require fast and responsive performance.

	One disadvantage of Go's garbage collector is that it can sometimes lead to higher memory usage, since the program may allocate more memory than it actually needs in order to avoid frequent garbage collection cycles. This can be mitigated by careful programming and by using tools like memory profilers to identify and eliminate memory leaks.

	Another disadvantage is that the garbage collector can sometimes introduce performance overhead, particularly in applications that have very high performance requirements. This can be addressed by tuning the garbage collector settings, but doing so requires a deeper understanding of how the garbage collector works.

	13. What are channels in Go, and how are they used?
	
	In Go, channels are a powerful mechanism for synchronizing the execution of concurrent goroutines and passing data between them. Channels can be thought of as typed pipes that allow goroutines to send and receive values of a particular type.

	To create a channel in Go, you can use the built-in make function with the chan keyword and specify the type of values that will be passed through the channel, for example:
	```
	ch := make(chan int)
	```
	This creates a channel ch that can be used to send and receive integer values. Values are sent on a channel using the <- operator, and received using the same operator with the channel name on the right-hand side:

	```
	ch <- 42 // Send the value 42 on the channel
	x := <-ch // Receive a value from the channel and store it in x
	```
	Channels can be used to implement a wide range of concurrent patterns, such as producer-consumer, pipeline, and fan-out/fan-in. For example, in a producer-consumer pattern, a producer goroutine can send data on a channel, while one or more consumer goroutines receive the data and process it:

	```
	func producer(ch chan int) {
	    for i := 0; i < 10; i++ {
		ch <- i
	    }
	    close(ch)
	}

	func consumer(ch chan int) {
	    for i := range ch {
		fmt.Println(i)
	    }
	}

	func main() {
	    ch := make(chan int)
	    go producer(ch)
	    go consumer(ch)
	    time.Sleep(1 * time.Second)
	}
	```
	In this example, the producer function sends integer values on the ch channel, while the consumer function receives the values and prints them to the console. The time.Sleep call at the end of the main function is used to give the goroutines time to execute before the program exits.

	Channels in Go provide a safe and efficient way to coordinate the execution of concurrent goroutines and communicate between them, making it easier to write scalable and efficient concurrent programs.

14. How do you handle errors in Go, and what are some best practices for error handling?

	In Go, errors are represented using the built-in error interface, which is defined as follows:

	```
	type error interface {
	    Error() string
	}
	```
	Functions in Go typically return an error as their last return value, which can be used to indicate whether the function succeeded or failed. To handle errors in Go, you can use the if err != nil idiom to check whether an error occurred, and take appropriate action based on the error:

	```
	result, err := someFunction()
	if err != nil {
	    // Handle the error
	} else {
	    // Use the result
	}
	```
	In Go, it is a best practice to handle errors explicitly, rather than ignoring them or passing them up the call stack. Some best practices for error handling in Go include:

	Always check for errors: Make sure to check for errors and handle them appropriately. Ignoring errors can lead to unexpected behavior and hard-to-debug issues.

	Wrap errors: When propagating an error up the call stack, wrap the error with additional context to make it easier to debug. You can use the fmt.Errorf function to create an error with a formatted message and the original error:

	```
	_, err := someFunction()
	if err != nil {
	    return fmt.Errorf("someFunction failed: %w", err)
	}
	```
	The %w verb is used to wrap the original error with additional context.

	Return errors as values: Functions in Go should return errors as values, rather than panicking or logging the error and continuing. This makes it easier to handle errors and provides a clear indication of whether a function succeeded or failed.

	Don't use errors as control flow: Avoid using errors as a mechanism for control flow in your code, such as using a specific error to indicate a certain condition. This can make your code harder to read and maintain.

	Use typed errors: Consider using typed errors instead of string errors to provide more information about the error. You can define your own error types by implementing the error interface:
```
type MyError struct {
    Msg string
}

func (e MyError) Error() string {
    return e.Msg
}
```

	In summary, error handling in Go involves checking for errors explicitly, wrapping errors with additional context, returning errors as values, and avoiding the use of errors as control flow. By following these best practices, you can write more robust and maintainable Go code.
	
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







