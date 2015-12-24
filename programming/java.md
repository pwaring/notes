# Java

## Commands

### javap

The `javap` command prints a description of a compiled class, provided that it is in the classpath. For example:

```
$ javap java.util.Stack
Compiled from "Stack.java"
public class java.util.Stack<E> extends java.util.Vector<E> {
  public java.util.Stack();
  public E push(E);
  public synchronized E pop();
  public synchronized E peek();
  public boolean empty();
  public synchronized int search(java.lang.Object);
}
```

## Filenames

Source files can only contain one public class, and the file must have the same name as the class with a `.java` extension (or a `.class` extension for byte code).

## Core Classes

Core classes (automatically in the classpath) include:

 * `java.lang`
 * `java.io`
 * `java.net`
 * `javax.swing`

However, only classes in `java.lang` do not require an `import` line.

## Variable types and modifiers

`final`: Value is assigned at declaration (or in constructor), after which its value cannot be changed.

## Inheritance

Classes can only extend one class, but can implement multiple interfaces.

## Default values for variables

Instance variables: `0`, `false` or `null`, depending on the type.

Local variables: No default value.

## Coding standards

Things to note:

 * Always use `this` when referring to an instance method or variable inside a class.
 * Each variable declaration should be on its own line - makes it easier to comment out, delete or add new variables.

## Threads

Objects can work with threads in one of two ways:

 * Subclass `Thread`.
 * Implement `Runnable` and pass object to the constructor of `Thread`, then call `Thread.start()` (which calls `Object.run()`).

Adding `syncronized` to a method means that a lock will be acquired before calling that method. The lock is at the object level, so only one syncronized method in the object can be running at any one time.

## Javadoc

Adding the `@deprecated` tag to a class, method or variable will cause a compiler warning if the component is used.

## Exceptions

In Java 7, there is a new 'try with resources' which can be used like so:

```
try (
  // Initialise resources such as Socket s = new Socket()
  )
{
  // do something
} catch ( Exception e ) {
  // handle exception
}
```

Resources initialised immediately after `try` will be closed when control leaves the block, either via an exception or successful completion. Resources are closed in the reverse order to their construction, and this behaviour is only supported for classes that implement `AutoCloseable`.

## Memory management

Java objects and their instance variables are allocated on the heap, but local variables are allocated on the stack.

## Graphical interfaces

Two standard packages available:

AWT: Attempts to mimic native look and feel for each platform. Lacks features such as trees as these are not present across all platforms.

Swing: Built on AWT, but implemented entirely in Java. Same interface across all platforms. Classnames broadly similar to AWT but start with J (e.g. `JButton` as opposed to `Button`). Multiple 'themes' are available, with Nimbus being the current best option for cross-platform interfaces as of Java 6.

Event objects are delivered to all objects which have registered themselves as listeners for that event. For example, to receive an `ActionEvent`, the object should register as an `ActionListener`.

### Splash screens

A splash screen can be added by providing the following information in a JAR manifest:

```
Manifest-Version: 1.0
Main-Class: MyClass
SplashScreen-Image: my-splash.png
```

### Desktop integration

`java.awt.Desktop` provides integration with the desktop environment.

### Menus

Menus are split into three components:

 * `JMenuBar`: Contains `JMenu`
 * `JMenu`: Contains `JMenuItem`
 * `JMenuItem`: Individual menu item.

Each menu item can have a mnemonic (`setMnemonic`) and an accelerator (`setAcceletor`).


## Articles

 * [Tuning Java Servers](http://www.infoq.com/articles/Tuning-Java-Servers)
