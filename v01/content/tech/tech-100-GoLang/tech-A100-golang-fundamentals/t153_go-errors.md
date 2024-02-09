---
title: GoLang errors
subtitle: Sentinel Errors & Wrapping/Unwrapping Errors with Code Example  
date: 2022-01-05
weight: 200
draft: false
type: "tech"
---
In Go, sentinel errors and wrapping/unwrapping errors are common practices for error handling. Sentinel errors in Go often involve using specific pre-defined values to represent errors, while wrapping and unwrapping errors involve creating custom error types and adding context to errors for better diagnosis.

## Sentinel Errors:
In Go, a common practice is to define package-level errors as constants for reuse. Here's an example:

```go
package main

import (
	"errors"
	"fmt"
)

var ErrDivideByZero = errors.New("division by zero")

func divide(a, b int) (int, error) {
	if b == 0 {
		return 0, ErrDivideByZero
	}
	return a / b, nil
}

func main() {
	result, err := divide(5, 0)
	if err != nil {
		if err == ErrDivideByZero {
			fmt.Println("Error: Division by zero!")
		} else {
			fmt.Println("Error:", err)
		}
	} else {
		fmt.Println("Result:", result)
	}
}
```


# Wrapping and Unwrapping Errors:
In Go, you can use the errors package or create custom error types to wrap and unwrap errors. Here's an example:

```go
package main

import (
	"errors"
	"fmt"
)

type CustomError struct {
	Context string
	Err     error
}

func (ce *CustomError) Error() string {
	return fmt.Sprintf("%s: %v", ce.Context, ce.Err)
}

func process(data string) (int, error) {
	// Some processing that may raise an exception
	result, err := strconv.Atoi(data)
	if err != nil {
		// Wrap the original exception in a custom exception
		return 0, &CustomError{Context: "Error processing data", Err: err}
	}
	return result, nil
}

func handleError() {
	_, err := process("abc")
	if err != nil {
		// Unwrap the original exception and handle it separately
		if customErr, ok := err.(*CustomError); ok {
			fmt.Printf("Caught custom error: %v\n", customErr)
			// Access the wrapped original exception
			originalException := customErr.Err
			fmt.Printf("Original exception: %v\n", originalException)
		} else {
			fmt.Println("Unhandled error:", err)
		}
	}
}

func main() {
	handleError()
}
```

In this example, CustomError is a custom error type that wraps the original error. The handleError function demonstrates how to unwrap and handle specific errors.
