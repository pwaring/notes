# C++

## Sample Makefile

```
CC=clang++
CFLAGS=-Weverything -std=c++11 -stdlib=libc++
LDFLAGS=
SOURCES=readfile.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=readfile

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.cpp.o:
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -rf *.o $(EXECUTABLE)
```

## Links

 * [The Definitive C++ Book Guide and List](http://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list)
 * [cplusplus.com](http://www.cplusplus.com/) - Good reference section.
