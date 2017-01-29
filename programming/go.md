# Go

## Variables

Variables are defined as:

```go
var name type = value
```

For example:

```go
var x string = "Hello"
```

The type can be inferred if an initial value is given, e.g.

```go
var x = "Hello"
```

or by using the `:=` operator:

```go
x := "Hello"
```

Constants can be defined by using the `const` keyword instead of `var`.

## Imports

Standard import notation:

```
import "fmt"
```

Multiple imports can be done either one line at a time or as a group:

```
import (
  "fmt"
  "math"
)
```

Names in packages are exported if they begin with a capital letter.

## Articles

 * [Best practices for a new Go developer](https://medium.com/@IndianGuru/best-practices-for-a-new-go-developer-8660384302fc)
 * [Go at Google: Language Design in the Service of Software Engineering](http://talks.golang.org/2012/splash.article)

## Talks

 * [Go for Java Programmers](https://talks.golang.org/2015/go-for-java-programmers.slide)

## Tutorials

  * [Learn Go in Y minutes](http://learnxinyminutes.com/docs/go/)
  * [Go by example](https://gobyexample.com/)
  * [A tour of Go](http://tour.golang.org/welcome/1)
  * [Effective Go](http://golang.org/doc/effective_go.html)
