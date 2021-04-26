### Makefile

A Makefile consists of a set of rules. A rule generally looks like this:
```
targets: prerequisites
   command
   command
   command
```
The targets are file names, seperated by spaces. Typically, there is only one per rule.

The commands are a series of steps typically used to make the target(s). These need to start with a tab character, not spaces. They are often bash commands.

The prerequisites are also file names, seperated by spaces. These files need to exist before the commands for the target are run. These are also called dependencies.

***

targets can be file names that will be created by the commands, or they can just be other names, in which case you will want to add a `.PHONY:` line listing all of the commands that don't actually correspond to a file and should be run even if a file of that name exists already.

`make clean` is a common command, often removing the build folder. It would look something like this:
```
clean:
    rm -rf build
.PHONY: clean
```

Another common one is `make env`, which could make the conda environment necessary for the repository to run.

Because of these functionalities, among others, a Makefile is an obvious way to improve the functionality of your repository.

***

Some makefiles have a target called “clean”. Run it via `make clean` to delete the files that make generated. For example:
```
clean:
    rm some_file
    rm -rf build
```

***

```
some_file:
    echo "This line will only print once"
    touch some_file
```
This example would make some_file the first time, and the second time notice it’s already made, resulting in
```
make: 'some_file' is up to date.
```

***

Thus, each command only runs if the target file doesn't exist.
Adding .PHONY to a target will prevent make from confusing the phony target with a file name. In this example, if the file “clean” is created, make clean will still be run. .PHONY is great to use, and can be used for all of the targets if you simply want to make some shortcuts for running certain commands.
```
.PHONY: clean
```

***

Making multiple targets and you want all of them to run? Make a all target and designate it as .PHONY
```
all: one two three
.PHONY: all
```

***

Double-Colon Rules are rarely used, but allow the same target to run commands from multiple targets.
If these were single colons, an warning would be printed and only the second set of commands would run.
```
all: blah

blah::
    echo "hello"

blah::
    echo "hello again"
```
***
Add an @ before a command to stop it from being printed
You can also run make with -s to add an @ before each line
```
all: 
    @echo "This make line will not be printed"
    echo "But this will"
```
***
The make tool will stop running a rule (and will propogate back to prerequisites) if a command returns a nonzero exit status.
DELETE_ON_ERROR will delete the target of a rule if the rule fails in this manner. This will happen for all targets, not just the one it is before like PHONY. It’s a good idea to always use this, even though make does not for historical reasons.
```
.DELETE_ON_ERROR:
all: one two

one:
    touch one
    false

two:
    touch two
    false
```

***

Recursively call a makefile. Use the special $(MAKE) instead of “make”
because it will pass the make flags for you and won’t itself be affected by them.
```
new_contents = "hello:\n\ttouch inside_file"
all:
    mkdir -p subdir
    echo $(new_contents) | sed -e 's/^ //' > subdir/makefile
    cd subdir && $(MAKE)

clean:
    rm -rf subdir
```

***

Reference variables using ${} or $()
```
x = dude

.PHONY: all
all:
    echo $(x)
    echo ${x}

    # Bad practice, but works
    echo $x
```
EXPORT_ALL_VARIABLES does what you might expect. It exports variables for outside use.
```
.EXPORT_ALL_VARIABLES:
```
Simply expanded allows you to append to a variable. Recursive definitions will give an infinite loop error.
```
one = hello
# one gets defined as a simply expanded variable (:=) and thus can handle appending
one := ${one} there
```
?= only sets variables if they have not yet been set
```
one = hello
one ?= will not be set
two ?= will be set
```
An undefined variable is actually an empty string!

Use += to append
```
foo := start
foo += more
```

***

There are many automatic variables, but often only a few show up:
```
hey: one two
    # Outputs "hey", since this is the first target
    echo $@

    # Outputs all prerequisites older than the target
    echo $?

    # Outputs all prerequisites
    echo $^

    touch hey

one:
    touch one

two:
    touch two

clean:
    rm -f hey one two
```

----------------------------------
Initially created by Ryan Johnson, December 2020.