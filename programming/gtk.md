# GTK

 * `gtk_widget_show()` will only show the widget passed as the parameter.
 Invisible children will not be shown, and if the widget's parent is invisible
 then the widget will not be shown until its parent is.
 * `gtk_widget_hide()` only marks the parameter widget as hidden. Although all
 child widgets are hidden by implication, they are not set as such, and so
 showing the widget again will result in all of its children being shown.
 * `gtk_widget_show_all()` recursively draws the widget and all its children.
 * `gtk_widget_hide_all()` recursives hides and sets the hidden flag on the
 widget and all its children.
 * `gtk_widget_set_sensitive` sets a widget as active or inactive. Children take
 their sensitivity from their parents and any change to the parent will
 automatically affect the children.
 * `gtk_window_set_icon_from_file` sets the file icon, and will be automatically
 resized as required.

## Signals and callbacks

Signals can be connected at any point within the application, including within
callback functions. However, it is sensible to initialise any critical callbacks
before calling `gtk_main()`.

The underscore and dash characters are interchangeable in signal names, so
"destroy_event" and "destroy-event" refer to the same signal.

`g_signal_connect()` returns a handler identifier which can be used with the
`g_signal_handler` functions.

## Simple Makefile

The following Makefile is sufficient to compile GTK 3 applications using clang
on Linux. This assumes that the GTK library has been registered with `pkg-config`,
which will be the case if you have installed your distribution's package.

```
CC=clang
CFLAGS=-Wall -Wextra -Werror $(shell pkg-config gtk+-3.0 --cflags)
LDFLAGS=$(shell pkg-config gtk+-3.0 --libs)
SOURCES=helloworld.c
OBJECTS=$(SOURCES:.c=.o)
EXECUTABLE=helloworld

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -rf *.o $(EXECUTABLE)
```

## Articles

 * [Building GTK apps for MS Windows on Linux](http://ricardo.ecn.wfu.edu/~cottrell/cross-gtk/)
 * [GTK+ tutorial](http://zetcode.com/tutorials/gtktutorial/)
 * [GTK vs Qt](http://www.wikivs.com/wiki/GTK_vs_Qt)
