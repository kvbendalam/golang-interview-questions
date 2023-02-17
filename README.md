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
8. What is Go, and why was it created?

	Go, also known as Golang, is an open-source programming language developed by Google. It was first publicly announced in November 2009, and the first stable version, Go 1.0, was released in March 2012.

	Go was created to address some of the shortcomings of existing programming languages, such as C and C++, by providing a more modern and efficient language that can handle large-scale software development projects. The language was designed with the following goals in mind:

	Simplicity: Go is designed to be simple and easy to learn, with a minimalistic syntax and a concise set of features that allow developers to write efficient and readable code.

	Performance: Go is designed to be fast and efficient, with built-in support for concurrency and garbage collection that make it well-suited for modern software development.

	Safety: Go includes features that make it easy to write safe and secure code, including strong typing, memory safety, and garbage collection.

	Openness: Go is an open-source language, with a vibrant community of developers and contributors who are constantly working to improve the language and its ecosystem.

	Overall, Go was created to provide a modern and efficient language that can handle the challenges of large-scale software development, while still being simple and easy to learn. Its popularity has grown rapidly in recent years, with many companies and developers using it for a wide range of applications, including web development, systems programming, and machine learning.

9. How does garbage collection work in Go, and what are some advantages and disadvantages of Go's garbage collector?

	Garbage collection in Go is a process by which the Go runtime manages memory allocation and deallocation for programs written in Go. The garbage collector runs automatically in the background, freeing up memory that is no longer being used by the program.

	The garbage collector in Go uses a mark-and-sweep algorithm, which works by first marking all of the objects that are still being used by the program. It then sweeps through the memory and deallocates any objects that were not marked. This process is repeated periodically to ensure that memory usage is kept under control.

	One advantage of Go's garbage collector is that it allows programmers to focus on writing code without having to worry about memory management. This can make it easier to write correct and reliable code, since it eliminates many of the potential bugs that can arise from manual memory management.

	Another advantage is that the garbage collector is optimized for low-latency, which means that it can perform garbage collection in a way that minimizes disruptions to the program's execution. This can be important for certain types of applications that require fast and responsive performance.

	One disadvantage of Go's garbage collector is that it can sometimes lead to higher memory usage, since the program may allocate more memory than it actually needs in order to avoid frequent garbage collection cycles. This can be mitigated by careful programming and by using tools like memory profilers to identify and eliminate memory leaks.

	Another disadvantage is that the garbage collector can sometimes introduce performance overhead, particularly in applications that have very high performance requirements. This can be addressed by tuning the garbage collector settings, but doing so requires a deeper understanding of how the garbage collector works.

10. What are channels in Go, and how are they used?
	
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

11. How do you handle errors in Go, and what are some best practices for error handling?

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
	
12. What is a goroutine in Go, and how does it differ from a thread?
	
	In Go, a goroutine is a lightweight, independently executing function that runs concurrently with other goroutines within the same address space. Goroutines are similar to threads in other programming languages, but they are implemented in a more lightweight and efficient way.

	In Go, a program starts with a single goroutine, which is created automatically when the program starts. Additional goroutines can be created using the go keyword followed by a function call, like this:

	```
	func main() {
	    go myFunction()
	    // ...
	}

	func myFunction() {
	    // ...
	}
	```

	
	When myFunction() is called with go, a new goroutine is created and myFunction() is executed in that goroutine concurrently with the main goroutine. The two goroutines can execute simultaneously and communicate with each other using channels or other synchronization mechanisms.

	One of the key differences between goroutines and threads is their memory usage. In most operating systems, threads require a relatively large amount of memory to maintain their execution context, which includes the stack, register values, and other information. In contrast, goroutines in Go are implemented as small, fixed-size stacks (typically a few kilobytes), and their execution contexts are stored on the heap, making them much more memory-efficient.

	Another difference between goroutines and threads is their scheduling model. In most operating systems, threads are scheduled by the operating system's scheduler, which is responsible for deciding when and where to run each thread. In contrast, goroutines in Go are scheduled by a built-in scheduler that is part of the Go runtime. The Go scheduler is responsible for assigning work to different available CPU cores and multiplexing goroutines onto those cores as efficiently as possible.

	Overall, goroutines in Go provide a lightweight, efficient, and convenient way to write concurrent programs, making it easier to take advantage of multiple cores and improve the performance of your applications.

13. Can you explain what closures are in Go, and how they work?
	
	In Go, a closure is a function value that references variables from outside its own scope. When a closure is created, it captures the variables it references and stores them in a data structure called a closure. The closure can then be passed around and executed independently, and it will still have access to the variables it captured, even if they are no longer in scope.

	Here's an example of a closure in Go:

	```
	func adder() func(int) int {
	    sum := 0
	    return func(x int) int {
		sum += x
		return sum
	    }
	}

	func main() {
	    a := adder()
	    fmt.Println(a(1))  // prints 1
	    fmt.Println(a(2))  // prints 3
	    fmt.Println(a(3))  // prints 6
	}

	```
	
	In this example, the adder function returns a closure that takes an int parameter and returns an int. The closure captures a variable called sum, which is initialized to 0 when adder is called. Each time the closure is called, it adds the input parameter to sum and returns the new value of sum.

	Closures in Go are often used for creating functions that generate other functions or for implementing functions with persistent state. For example, you could use a closure to implement a counter that remembers its state between calls:

	```
	func counter() func() int {
	    count := 0
	    return func() int {
		count++
		return count
	    }
	}

	func main() {
	    c := counter()
	    fmt.Println(c())  // prints 1
	    fmt.Println(c())  // prints 2
	    fmt.Println(c())  // prints 3
	}

	```
	
	
	In this example, the counter function returns a closure that takes no parameters and returns an int. The closure captures a variable called count, which is initialized to 0 when counter is called. Each time the closure is called, it increments the value of count and returns it.

	Overall, closures in Go provide a powerful and flexible way to write higher-order functions and to create functions with persistent state. By capturing variables from their enclosing scopes, closures make it possible to write more expressive and concise code in a wide range of situations.


14. What is a pointer in Go, and how are they used?

	In Go, a pointer is a variable that stores the memory address of another variable. Pointers are used to pass values by reference, allowing functions to modify the original values instead of just receiving a copy.

	In Go, a pointer is represented by the * operator, which is used to declare a pointer type or to access the value of a pointer. Here's an example of how to declare and use a pointer in Go:
	

	```
	func main() {
	    var x int = 10
	    var ptr *int = &x

	    fmt.Println(x)    // prints 10
	    fmt.Println(*ptr) // prints 10

	    *ptr = 20
	    fmt.Println(x)    // prints 20
	    fmt.Println(*ptr) // prints 20
	}

	```
	
	
	In this example, we declare an integer variable x and a pointer variable ptr that points to the memory address of x. We use the & operator to get the address of x and assign it to ptr. We can then access the value of x indirectly using the * operator applied to ptr.

	We can also modify the value of x indirectly by assigning a new value to the memory address pointed to by ptr. When we modify *ptr, we are modifying the value of x itself.

	Pointers in Go are commonly used for passing large or complex data structures between functions, since copying these structures can be time-consuming and memory-intensive. Pointers are also used in Go for memory management, allowing programs to allocate and deallocate memory dynamically.

	However, pointers can also be a source of bugs and vulnerabilities, since incorrect use of pointers can cause memory leaks, data corruption, and security issues. To avoid these problems, it's important to follow best practices when working with pointers in Go, such as using nil pointers to indicate uninitialized or invalid values, avoiding pointer arithmetic and casting, and using the new and make functions to allocate memory safely.

15. What is the difference between a slice and an array in Go?
	
	In Go, an array and a slice are both used to store a sequence of values of the same type, but they differ in several important ways.

	An array is a fixed-size data structure that stores a specific number of elements of a specific type. The size of an array is fixed at compile time, and cannot be changed at runtime. Here's an example of how to declare and initialize an array in Go:

	```
	var a [3]int          // declares an array of 3 integers
	a[0] = 1              // sets the first element to 1
	a[1] = 2              // sets the second element to 2
	a[2] = 3              // sets the third element to 3
	fmt.Println(a)        // prints [1 2 3]
	
	```


	A slice, on the other hand, is a dynamic data structure that can grow or shrink in size at runtime. A slice is a view into an underlying array, and is defined by a starting and ending index. Here's an example of how to declare and initialize a slice in Go:
	
	
	```
	var s []int = []int{1, 2, 3}    // declares and initializes a slice of 3 integers
	fmt.Println(s)                  // prints [1 2 3]
	```
	
	Slices can also be created by slicing an existing array or slice using the [] operator. For example:
	
	
	```
	a := [5]int{1, 2, 3, 4, 5}
	s := a[1:4]        // creates a slice that includes elements 2, 3, and 4
	fmt.Println(s)     // prints [2 3 4]
	```
	
	One key difference between arrays and slices is that slices are passed by reference, while arrays are passed by value. This means that when you pass a slice to a function, you are actually passing a pointer to the underlying array, rather than making a copy of the slice. This can be more efficient than passing arrays by value, especially for large arrays.

	Another difference between arrays and slices is that slices have some built-in functions that make them more convenient to work with. For example, the append function can be used to add elements to a slice, and the copy function can be used to copy elements between slices.

	Overall, while arrays and slices are both used to store sequences of values in Go, they have different sizes and characteristics, and are used in different situations. Arrays are useful for storing fixed-size data that does not change, while slices are more flexible and can be used for storing dynamic data that can grow or shrink in size.


17. How do you handle dependencies in Go, and what are some tools that you can use for dependency management?
18. What are some common concurrency patterns in Go, and how are they used?
19. How to compare two slices in golang?
20. How to compare two structs in golang?
21. How to compare two maps in golang?

22. What is the difference between parallelism and concurrency?
	
	Parallelism and concurrency are related but distinct concepts in computer science.

	Concurrency refers to the ability of a system to handle multiple tasks or processes at the same time, regardless of whether those tasks are actually executing at the same time. In a concurrent system, tasks may be executed in parallel, but they may also be executed in an interleaved or overlapping fashion, depending on the specific scheduling algorithm used by the system. A good real-world example of concurrency is a web server, which handles many requests from clients at the same time, but does not necessarily process all of those requests in parallel.

	Parallelism, on the other hand, refers specifically to the ability of a system to execute multiple tasks or processes simultaneously, using multiple processing units. In a parallel system, tasks are executed in parallel, with each task running on a separate processing unit. A good real-world example of parallelism is a high-performance computing cluster, which uses multiple processors or nodes to execute a single large computational task in parallel.

	To summarize, concurrency is about managing multiple tasks or processes, while parallelism is about executing those tasks in parallel on separate processing units. In many cases, concurrency can be achieved without parallelism, but parallelism always requires some degree of concurrency.

	Here are some additional real-world examples of concurrency and parallelism:

	A spreadsheet program that recalculates formulas in real-time while the user is editing the data is an example of concurrency. The program is able to handle multiple input events (such as mouse clicks and keystrokes) concurrently, but it does not necessarily execute those events in parallel.
	
	A video game that uses a separate thread to load assets (such as textures and models) in the background while the main game loop runs is an example of concurrency. The game is able to handle both gameplay logic and asset loading concurrently, but it does not necessarily execute those tasks in parallel.
	
	A machine learning algorithm that distributes training data across multiple processors or nodes to speed up the training process is an example of parallelism. The algorithm is able to execute multiple training iterations in parallel, with each iteration running on a separate processing unit.

23. What is statically typed languages?
	
	A statically typed language is a programming language where variables are bound to a specific data type at compile time, and this data type cannot be changed during the execution of the program. The type of a variable must be declared explicitly, and the compiler checks whether the types of variables are consistent and compatible with each other.

	In statically typed languages, the data types are usually defined by the language specification, and the compiler uses this information to generate efficient machine code that can run the program. This approach provides better performance and helps catch type-related errors at compile time, before the program is run, which can help prevent certain types of bugs.

	Some examples of statically typed languages include Java, C++, C#, Swift, and Go. These languages are often used for large, complex software projects that require high performance and reliability, such as operating systems, databases, and web applications. However, the rigid type checking can also make statically typed languages less flexible and harder to work with for rapid prototyping and experimentation.

24. What is dynamically typed languages?
		A dynamically typed language is a programming language where variables are not bound to a specific data type at compile time, but instead, the type of a variable is determined at runtime based on the value it is assigned. The type of a variable does not need to be declared explicitly, and it can change dynamically during the execution of the program.

	In dynamically typed languages, the interpreter or runtime system infers the data type of a variable based on its current value and how it is being used in the program. This approach allows for more flexibility and faster development times since the programmer can change the type of a variable on the fly, without having to worry about type declarations or compiler errors.

	Some examples of dynamically typed languages include Python, JavaScript, Ruby, and PHP. These languages are often used for rapid prototyping, scripting, and web development, where speed of development and flexibility are often more important than performance.

	However, dynamic typing can also make the code harder to debug and maintain, as errors related to data types can go undetected until runtime, and the lack of type checking can make it harder to understand how variables are being used in the code.

25. What is race condition?
	
	A race condition is a situation that occurs in computer programs when two or more threads or processes access a shared resource or data at the same time, and the final outcome of the program depends on the order in which these access occur. The result of the program may be dependent on the timing of the events, and can be unpredictable and non-deterministic.

	Race conditions can occur when multiple threads or processes are trying to modify a shared variable, file, or other resource without proper synchronization. When two threads or processes try to modify the same variable or resource at the same time, the final outcome can be different depending on which thread or process executes first. This can result in unexpected program behavior, crashes, or data corruption.

	Race conditions are often difficult to reproduce and debug, as they can be influenced by a number of factors, such as the speed of the computer, the number of threads or processes involved, and the exact timing of the events. To avoid race conditions, programs must use proper synchronization techniques, such as locks, semaphores, or other mechanisms that ensure that only one thread or process can access a shared resource at a time.
	
27. What is defer in golang?
	
	In Go, defer is a statement that is used to schedule a function call to be executed at the end of the current function or block, just before it returns. The defer statement is often used to release resources, such as closing a file, unlocking a mutex, or closing a network connection, to ensure that they are properly cleaned up when the function or block exits, regardless of the reason for the exit, such as a normal return, a panic, or a runtime error.

	When a defer statement is executed, the arguments to the function are evaluated immediately, but the actual function call is delayed until the end of the enclosing function or block. This means that the deferred function call will be executed in reverse order of their appearance in the code, meaning the last deferred function call will be executed first and the first deferred function call will be executed last.

	Here is an example that demonstrates the use of defer:

	```
	func foo() {
	    defer fmt.Println("deferred call")
	    fmt.Println("normal call")
	}
	```
	
	In this example, the foo function prints "normal call" and schedules a deferred function call to print "deferred call". When the foo function returns, the deferred function call is executed, and "deferred call" is printed.

	Defer statements are commonly used in Go to ensure that resources are properly cleaned up, even in the presence of errors or panics, which can help make Go programs more robust and reliable.
	
29. What is panic in golang?

		In Go, panic is a built-in function that is used to cause a program to immediately stop execution and start a panic, which is an unrecoverable error that can crash the program. When a panic occurs, the program will unwind the stack, meaning that it will stop executing the current function and continue to unwind the call stack until it reaches a deferred function or the top of the stack.

	Panics are often used to indicate that a program has encountered an unrecoverable error condition, such as an out-of-memory condition, a division by zero, or an attempt to access an invalid memory address. When a panic occurs, the program will terminate and print a stack trace that shows the sequence of function calls that led to the panic, along with the file names and line numbers of the offending code.

	Here is an example of using panic:
	
	```
	func divide(a, b int) int {
	    if b == 0 {
		panic("division by zero")
	    }
	    return a / b
	}
	```
	
	In this example, the divide function checks if the second argument is zero and panics if it is, using a string message to indicate the error. If the divide function is called with a zero second argument, it will cause a panic and stop the program.

It is important to note that panics are only used for unrecoverable errors, and should not be used for normal error handling. Go has a separate error handling mechanism, based on returning errors as values, which is preferred for normal error conditions.
	
31. What is the use of recover in golang?
		
		In Go, recover is a built-in function that is used to recover from a panic and resume normal execution. When a panic occurs, the program will unwind the stack and call any deferred functions, but if a deferred function calls recover, the panic will be stopped and the program will continue executing normally.

	The recover function can only be called from within a deferred function, and it returns the value that was passed to the panic function, allowing the program to examine the error and take appropriate action. If the recover function is called from a non-deferred function, or if it is called when there is no active panic, it will return nil.

	Here is an example that demonstrates the use of recover:
	
	```
	func foo() {
	    defer func() {
		if r := recover(); r != nil {
		    fmt.Println("recovered from panic:", r)
		}
	    }()
	    panic("test panic")
	}
	```
	
	In this example, the foo function panics with a string message, but the deferred function uses recover to catch the panic and print a message. When the foo function is called, it will panic and print the message, but the program will not terminate and will resume normal execution after the deferred function completes.

	The recover function is often used in conjunction with defer to handle panics and allow programs to gracefully recover from errors, especially in long-running programs such as servers or daemons. However, it is important to note that recover should only be used for handling unexpected panics, and should not be used for normal error handling. The preferred way to handle normal errors in Go is by returning error values as part of the function's return signature.

33. Type assertion in golang?

	In Go, type assertion is a way to check whether an interface value holds a specific underlying concrete type, and to extract the value of that type. It is often used to perform a runtime type check of an interface value, and to access its underlying concrete value if it matches the desired type.

	The syntax for type assertion in Go is as follows:
	
	```
	x, ok := y.(T)
	```
	
	where y is an interface value, T is a concrete type, and x is a variable of type T. The second return value, ok, is a boolean that indicates whether the type assertion succeeded or failed.

	If the type assertion succeeds, x will be set to the underlying concrete value of type T held by the interface value y, and ok will be set to true. If the type assertion fails, x will be set to the zero value of type T (i.e., nil for pointers, 0 for numeric types, false for bools, and so on), and ok will be set to false.

	Here is an example that demonstrates the use of type assertion in Go:

	```
	func printInt(x interface{}) {
	    if n, ok := x.(int); ok {
		fmt.Println("x is an int:", n)
	    } else {
		fmt.Println("x is not an int")
	    }
	}

	func main() {
	    printInt(42)
	    printInt("hello")
	}

	```
	
	In this example, the printInt function takes an interface value x, and uses a type assertion to check whether it holds an int value. If the type assertion succeeds, it prints a message indicating that x is an int, along with its value. If the type assertion fails, it prints a message indicating that x is not an int.

	When the printInt function is called with an int value, the type assertion succeeds and the function prints "x is an int: 42". When the function is called with a string value, the type assertion fails and the function prints "x is not an int".

35. what is rune in golang?

	In Go, a rune is an alias for the int32 type, and represents a Unicode code point. A Unicode code point is a numerical value that uniquely identifies a character in the Unicode standard.
	
	Because Go uses Unicode to represent strings, rune is often used to represent individual characters in a string. For example, you can use the range keyword with a string to iterate over its individual runes:
	
	```
	s := "hello, 世界"
	for _, r := range s {
	    fmt.Printf("%c", r)
	}
	```
	
	In this example, the range statement iterates over the string s and extracts each individual rune. The %c format verb is used to print the character represented by each rune.

	rune is a built-in type in Go, and can be used wherever an int32 value is expected. For example, you can declare a slice of runes like this:
	
	
	```
	var r []rune = []rune{'h', 'e', 'l', 'l', 'o', ',', ' ', '世', '界'}
	```
	
	In general, rune is used in Go to represent Unicode characters, and provides a convenient way to work with Unicode strings and characters.
	
37. Object oriented principles in golang?

	Go is not a pure object-oriented programming language like Java or C++, but it supports some of the core principles of object-oriented programming, such as encapsulation, abstraction, and composition.

	One of the key mechanisms for achieving encapsulation in Go is the use of exported and unexported identifiers. By convention, any identifier that begins with a capital letter is exported from its package and can be accessed by other packages, while any identifier that begins with a lowercase letter is unexported and can only be accessed within its own package. This allows you to control the visibility and access of data and functions in your code.

	Go also supports abstraction through the use of interfaces. An interface is a set of method signatures that define a contract for a specific behavior, without specifying how that behavior is implemented. This allows you to write code that is decoupled from specific implementations, and can be used with any type that satisfies the interface. By convention, Go interfaces are named with a single method, followed by the "-er" suffix, such as io.Reader or http.Handler.

	Composition is another important principle of object-oriented programming that Go supports through the use of struct embedding. Struct embedding allows you to create new types by embedding one or more existing types as fields, and then accessing their methods and fields directly. This can be used to create more complex data structures and behaviors by combining smaller, more focused types.

	In summary, while Go is not a pure object-oriented language, it provides several features that support the core principles of encapsulation, abstraction, and composition. By using these features effectively, you can write code that is modular, flexible, and maintainable.
	
	
39. Compiled programming vs Interpreted programming
	
	Compiled programming and interpreted programming are two different ways of executing computer programs.

	In compiled programming, the source code of a program is translated into machine code by a compiler before the program is executed. The resulting machine code is specific to the hardware and operating system on which it is compiled, and can be directly executed by the computer without the need for any further translation or interpretation. Examples of compiled programming languages include C, C++, and Rust.

	In interpreted programming, the source code of a program is interpreted by an interpreter at runtime. The interpreter reads and executes the source code line by line, translating each line into machine code on the fly. Because the interpreter is translating the code at runtime, the resulting machine code can be specific to the hardware and operating system on which the program is executed. Examples of interpreted programming languages include Python, Ruby, and JavaScript.

	One advantage of compiled programming is that the resulting machine code can be highly optimized for the specific hardware and operating system on which it is compiled, leading to faster execution times. Compiled programs are also typically easier to distribute, since they do not require a compiler or interpreter to be installed on the target system.

	One advantage of interpreted programming is that it can be more flexible and easier to debug, since the interpreter can execute the source code directly and provide error messages and debugging information in real time. Interpreted programs are also typically more portable, since they can be executed on any system with an interpreter for the specific programming language.

	In summary, compiled programming and interpreted programming are two different ways of executing computer programs, each with their own advantages and disadvantages. The choice of programming approach depends on the specific requirements of the program and the target system on which it will be executed.
	
41. Compare the two variables in golang . 
	a = 10
	b = 10
	
	
	
34. Compare these two maps 
	a = []int{1}
	b = []int{1}
	
	```
	fmt.Println(a==b)
	```
	
	
35. Compare two maps
	a = map[string]string{"A": "B"}
	b = map[string]string{"A": "B"}
	
	
	
36. Output of the following:
	a := []int{5, 7}
	b := []int{6, 6}
	check := a
	copy(a, b)
	fmt.Println(a, b, check)
	
	

37.What is the out for the following: 
	a := []int{5, 7}
	b := []int{6, 8}
	check := a
	a = b
	fmt.Println(a, b, check)

38. Arrange the key in sorted order:
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

39. Question: 
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
  
  
40. Type conversion from string to integers

42. How to run different applications in same port 


43. How to optimize data base queries


44. How to copy postgres table 


45. How to write unit tests in golang







