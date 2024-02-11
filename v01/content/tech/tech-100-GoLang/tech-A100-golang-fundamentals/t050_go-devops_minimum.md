---
title: DevOps Go Engineering
subtitle: Fundamentals that you should just know for interviews 
date: 2022-01-05
weight: 50
draft: false
type: "tech"
Links: [    "https://go.dev/doc/tutorial/workspaces",                   "https://go.dev/ref/mod"
]

---

If you are going for a golang devops interview, these are the things I would ask...   and you should know.


# About being a good Team member - DEV/OPS
Git and version control is fundamental to being a team player.  Understand what version/source control is and how to use it.  very important.

## resources: 
{https://git-scm.com/}


1. Understand Git repo's
2. Branching
3. Pull Requests
4. Merge 
5. Rebase
6. Local vs remote repos
7. Have a github, bitbucket or other git repo, and put up some interesting examples.  
8. Fork
9. understand GIT CLI
10. Configure GIT to use with a remote repo like github



## As a golang / rust developer, 
Understand how the ** go.mod ** uses git remotes as part of a microservices project.

## Summary
As a Dev/Ops engineer on a team. You should understand the development ceremony of 
1. Create a Feature branch off of Master.
2. Develope the code
3. Create update the test Unit cases and confirm they pass
4. Push your branch to Remote
5. Confirm Unit and Integration is passing.
6. Before a PR ( Pull Request ) to master, you should clean up the commit comments using rebase.  Remember that you are asking for your team mates to Give you the "LGTM" ( looks good to me).  Your work will reflect on everyone in your team and teams around you.
7. You should be involved in doing PR reviews of your team members. PR review has three objectives:
    - Comment on their coding style, leave remarks on what needs to me cleaned up, make sugestions.  
    - Understand what the code does so you become a redundant engineering resource. 
    - Learn what your team mates are doing so you can be productive during standups. 
    - Stop bad code before it is permitted into the Mast branch.  

## Go TESTING

TODO:  short bit about unit and integration testing.


## Go Subjects to study
That will probably be on the interview. 
This web site is a very good place to learn by example:
https://gobyexample.com/

But these are the traditional questions.

1. Concurancy
    - Go Routines
    - Probably the first question asked.
    - Any FUnction can run as a go routine by adding `go functionname`
    - Goroutines are lightweight threads of execution that run concurrently with other goroutines in a Go program. They are managed by the Go runtime scheduler, which schedules and multiplexes them onto a small number of OS threads
    - understand what makes Go Routines special vs Threads on other languages.
    - https://dev.to/gophers/what-are-goroutines-and-how-are-they-scheduled-2nj3#:~:text=Any%20function%20in%20go%20can%20be%20run,really%20naive%20use%20might%20look%20as%20follows:.




2. Defer
    - Defer is used to ensure that a function call is performed later in a program’s execution, usually for purposes of cleanup.
```go
  f := createFile("/tmp/defer.txt")
    defer closeFile(f)
```


3. Regular Expressiong
Go has built in support for regulat expressions.	
```go
import (
    "regexp"
)
func main() {
    //This tests whether a pattern matches a string.
    match, _ := regexp.MatchString("p([a-z]+)ch", "peach")
    fmt.Println(match)
}
```
review this:
https://en.wikipedia.org/wiki/Regular_expression

https://gobyexample.com/regular-expressions


4. URL Parsing
https://gobyexample.com/url-parsing

```go
	Run codeCopy code
package main
import (
    "fmt"
    "net"
    "net/url"
)
	
func main() {
  s := "postgres://user:pass@host.com:5432/path?k=v#f"
Parse the URL and ensure there are no errors.

    u, err := url.Parse(s)
    if err != nil {
        panic(err)
    }
}
```


5. String Formating
https://gobyexample.com/string-formatting

```go
import (
    "fmt"
    "os"
)
```

6. Line Filters
https://gobyexample.com/line-filters


A line filter is a common type of program that reads input on stdin, processes it, and then prints some derived result to stdout. grep and sed are common line filters


7. context
https://gobyexample.com/context
https://pkg.go.dev/context
https://www.digitalocean.com/community/tutorials/how-to-use-contexts-in-go

Cotext is basically a basket of data with added functionality. used in http and often go routines.  

```go
package main

import (
	"context"
	"fmt"
)

func doSomething(ctx context.Context) {
	fmt.Println("Doing something!")
}

func main() {
	ctx := context.TODO()
	doSomething(ctx)
}
```


8. Interfaces
https://gobyexample.com/interfaces


9. Generics
https://gobyexample.com/generics


10. Channels
- should be discussed with go routines.
- Channels are the pipes that connect concurrent goroutines. You can send values into channels from one goroutine and receive those values into another goroutine


11. Channel Synch
-  Wait groups
https://gobyexample.com/channel-synchronization


12. Channel direction
- https://gobyexample.com/channel-directions


13. Select
Go’s select lets you wait on multiple channel operations. Combining goroutines and channels with select is a powerful feature of Go.
https://gobyexample.com/select


14. closing channels
https://gobyexample.com/closing-channels

15. Structs

16. Interfaces

17. Make
 The built-in function make(T, args) serves a purpose different from new(T). It creates slices, maps, and channels only, and it returns an initialized (not zeroed) value of type T (not *T). The reason for the distinction is that these three types represent, under the covers, references to data structures that must be initialized before use. A slice, for example, is a three-item descriptor containing a pointer to the data (inside an array), the length, and the capacity, and until those items are initialized, the slice is nil. For slices, maps, and channels, make initializes the internal data structure and prepares the value for use.

18. Arrays

19. Slices

20. Maps
- Key value pairs

21. Multi Dimentional Slices

22. Constants
- cannot be changed because set at compile time.

23. Init function

24. Pointers vs Values

25. Byte Slice

26. Interfaces

27. Errors

28. WEB SERVICES
```go
    "html/template"
    "net/http"
```

29. JSON Marshal and unMarshal
https://gobyexample.com/json


# REST servers
Be prepaired to build an HTTP server. 
https://www.jetbrains.com/guide/go/tutorials/rest_api_series/stdlib/
 You should know the http package as well as others.
I like this article using gin framework
https://go.dev/doc/tutorial/web-service-gin


## Basically..
- know everything in :
https://gobyexample.com/

- Look over ALL of the Standard Libraries
https://pkg.go.dev/std




## REST
Go 


## Awsome Go
A currated list of extended packages
https://github.com/avelino/awesome-go



## CICD
Writing code is one thing, Deployment ceremonies are another
You should understand a CICD platform.  Jenkins is almost everywhere. I use GitHub Actions, which is very similar.

https://www.jenkins.io/
https://docs.github.com/en/actions

One way to learn, other than reading the documentation, is to review Github code, which includes the CICD YAML files.


## DOCKER
A containerization system
https://www.docker.com/


## Kubernetes 
also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.
https://kubernetes.io/


## Messaging, Event Streaming, KeyValue Stores
Understand the use of Messaging and benefits.

- Kafka,
https://kafka.apache.org/intro

- Cassandra

- RabitMQ

- AWS SQS, 

## DataBase SQL and NoSQL
The usual suspects like Postgress and mySQL.
You should also be familiar with noSQL;s

AWS - DynamoDB
Azure - CosmoDB
    - which is also a DocumentDB
Perhaps MONGODB
Redis
https://redis.com/




Adding to this all the time















