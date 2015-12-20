# C Sharp

## Keywords

`static class`: The given class cannot be instantiated.

`readonly [type]`: Variable can only be modified/set in the constructor.

`const [type]`: Variable set at compile time, can only be a standard type (no objects).

## Hello World

```
using System;

public class HelloWorld
{
  public static void Main()
  {
    Console.WriteLine("Hello World");
  }
}
```

## Mono

Compiling:

```
mcs hello.cs
```

Add `-pkg:dotnet` for standard .NET libraries (e.g. Winforms).

Executing:

```
mono hello.exe
```
