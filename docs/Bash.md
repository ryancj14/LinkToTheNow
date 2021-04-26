### Linux Command Layout and Functions
* pwd – prints the current working directory
* clear – clears the terminal
* ls [options] [location] – lists contents of directory (at current directory if none is given)
* cd [location] – changes current directory to location (or to user directory if none is given)
* file [location] – obtain info about what type of file it is
* man \<command to look up> – manual pages
* mkdir [options] \<Directory> – makes a directory in that place
* rmdir [options] \<Directory> - removes a directory from that place
* cp [options] \<source> \<destination> - copies the file to a new location
* mv [options] \<source> \<destination> - moves the file to a new location
* rm [options] \<file> - removes a file
* vi \<file> - open a file to edit
* cat \<file> - concatenate multiple files (or just view one)
* less \<file> - view file (for viewing a multipage file)
* chmod [permissions] [path] – changes the permissions of a file
* head [-number of lines to print] [path] – prints the first so many lines of the file (default 10)
* tail [-number of lines to print] [path] – prints the last so many lines of the file (default 10)
* sort [-options] [path] – sorts the data in each line (default is an alphabetical sort)
* nl [-options] [path] – puts a number before each line
* wc [-options] [path] – gives a word counts, and a character and line count
* cut [-options] [path] – gives the data from the desired columns
* sed \<expression> [path] – allows us to do a search and replace on our data
* uniq [options] [path] – removes duplicate lines from the data
* tac [path] – prints data backwards (last line to first line)
* egrep [command line options] \<pattern> [path] – prints every line containing the given pattern
* top – shows what processes are currently running with real-time data
* ps [aux] – shows a complete system view of processes running
* kill [signal] \<PID> – kills a process
* sleep [number] – waits that number of seconds
* jobs – displays a list of current jobs running in the background
* fg [number] – moves a background process into the foreground.
* echo \<message> – displays a message
* which \<program> - finds out where a program is located        
* date – prints the date
* yes [message] – prints the message (default is “y”) over and over again until you command-c
* read – take an input from the user and store it in a variable
* ip addr - check network connection and get ip address

### Easy Place to Remember Functions and Options of Commands - Further Details
 
* **pwd** – print working directory
* **clear** – clears terminal
* **echo** - displays (echos) what is given
* **ls** – lists
    * -l => long list (w/ details including permissions)
    * -a => all including hidden files
* **cd** – changes directories
* **file** – obtains file info
* **mkdir** – make directory
    * -p => and non-existent  parent directories
* **rmdir** – remove directory
    * -p => and empty parent directories up the line
* **man** – provides the manual for a command
    * q – quit
* **cp** – copy file
    * -r => and everything inside it
* **mv** – move file (or rename)
* **rm** – remove file
    * -r => and everything inside it
    * -i => gives a prompt before each file remove so you may cancel it
* **vi** – open editing tool (two modes – insert and edit)
    * insert mode    
        * esc – returns to edit mode
        * arrow keys – move the cursor around
        * other keys – insert that text
    * edit mode   	
        * i – goes to insert mode
        * arrow keys ( or h, j, k, l ) – move the cursor around (left, down, up, right)
        * b – move to beginning of previous word (type number first to go back that many words)
        * w – move to the beginning of the next word (type number first to go forward that many words)
        * G – move to the last line (type number first to move to that line)
        * ^ – move cursor to the beginning of current line
        * $ – move cursor to the end of current line
        * { – move backward one paragraph
        * } – move forward one paragraph
        * x – delete a character (type number first to delete that many characters)
        * dd – delete the current line
        * u – undo the last action
        * ZZ – save and exit
        * :set nu [enter] – turns on number lines
        * :set nocompatible - fix the issue of arrow keys not working in insert mode
        * :q! [enter] – discard all changes since the last save, and exit
        * :w [enter] – save file but don’t exit
        * :wq [enter] – save and exit 
* **cat** – concatenate or view files
* **less** – view a file
    * arrow keys – move the cursor around
    * SpaceBar – go forward one page
    * b – go back a page
    * q – quit
* **chmod** – changes modification permissions
    * [ugoa][+-][rwx] => grant(+)/revoke(-) read/write/execute permissions to user/group/others/all
        * (ex. chmod ug+rw [path] – grants read and write permissions to user and group)
    * [0-7][0-7][0-7] => shorthand representing the binary numbers setting all permissions
        * (ex. chmod 750 [path]– sets permissions as rwxr-x--- (the equivalent of 111101000))
* **head** – prints the first ten lines of the file
    * -[number] => designates a specific number of lines to print
* **tail** – prints the last ten lines of the file
    * -[number] => designates a specific number of lines to print
* **sort** – sorts the data in the file alphabetically
* **nl** – numbers each line of the file
    * -s [text] => specifies what should be printed after each number (before the line of text)
    * -w [number] => specifies how much padding to put before each number
* **wc** – word count (gives a line, word, and character count of the file)
    * -[lwc] gives only the line count, word count, or character count
* **cut** – cuts the data into fields and only display the specified fields
    * -f [numbers separated by commas] => columns to be shown
    * -d [text] => what separates the columns
    * -c => characters to display
* **sed** – stream editor (do a search and replace on the data
    * `‘s/[text to be replaced]/[text to replace it with]/[g]` => g is optional and if present replaces every instance instead of just the first one encountered
* **uniq** – prints all unique lines
* **tac** – cat backwards, prints last line to first line
* **egrep** – prints every line containing the pattern
* **top** – shows what processes are currently running
* **ps aux** – shows complete system view of processes
* **kill** – kills a signal
* **sleep** – sleeps for a number of seconds
* **jobs** – displays current jobs running in the background
* **fg** – moves a background process into the foreground.
* **echo** – displays a given message
* **which** – displays the location of a program (like bash itself)
* **date** – prints the date
* **yes** – prints y until you press control-c to cancel
* **read** – reads a user input into a variable
* **ip addr** - get ip address
* `yes "$(seq 1 20)" | while read digit; do echo digit; sleep 1; done` 
    * this is essentially a counter
* `yes long line of meaningless text for file padding | head -50 > test.txt`
    * fills a file with 50 lines of given text
* `sudo shutdown -r now`
    * shuts the computer down now and restarts it
* **\<ctrl> + c** – universal sign for cancel in Linux

### IMPORTANT CONCEPTS
* Relative path
    * A file or directory location relative to where we currently are in the file system.
* Absolute path
    * A file or directory location in relation to the root of the file system.
* Everything is a file under Linux
    * Even directories.
* Linux is an extensionless system
    * Files can have any extension they like or none at all.
* Linux is case sensitive
    * Beware of silly typos.
* The man pages are your friend.
    * Instead of trying to remember everything, instead remember you can easily look stuff up in the man pages.
* No undo
    * The Linux command line does not have an undo feature. Perform destructive actions  carefully.
* Command line options
    * Most commands have many useful command line options. Make sure you skim the man page for new commands so you are familiar with what they can do and what is available.
* No mouse
    * vi is a text editor where everything is done on the keyboard. If you can touch type, then this is great. If not, then maybe you should think about learning.
* Edit commands
    * There are many of them. Practice is the key to remember the most commonly used and useful ones.
* Wildcards
    * \* – represents zero or more characters
    * ? – represents a single character
    * […] – represents a range of characters 
        * (ex. [abc] could be ‘a’ or ‘b’ or ‘c’)
    * [^…] – represents a range of characters not including the ones shown
        * (ex. [^abc] could be anything but ‘a’, ‘b’, or ‘c’) 
    * Anywhere in any path
* Wildcards may be used at any part of a path.
* Wherever a path is used
* Because wildcard substitution is done by the system, not the command, they may be used wherever a path is used.
* Security
    * Correct permissions are important for the security of a system.
* Usage
    * Setting the right permissions is important in the smooth running of certain tasks on Linux.
* Processing
    * Filters allow us to process and format data in interesting ways.
* Man Pages
    * Most of the programs we looked at have command line options that allow you to modify their behavior.
* Regular Expressions
    * A powerful way to identify particular pieces of information.
    * . – a single character.
    * ? – the preceding character matches 0 or 1 times only.
    * \* – the preceding character matches 0 or more times.
    * \+ – the preceding character matches 1 or more times.
    * {n} – the preceding character matches exactly n times.
    * {n,m} – the preceding character matches at least n times and not more than m times.
    * [agd] – the character is one of those included within the square brackets.
    * [^agd] – the character is not one of those included within the square brackets.
    * [c-f] – the dash within the square brackets operates as a range. In this case it means either the letters c, d, e or f.
    * () – allows us to group several characters to behave as one.
    * | (pipe symbol) – the logical OR operation.
    * ^ – matches the beginning of the line.
    * $ – matches the end of the line.
    * Streams
    * Every program you may run on the command line has 3 streams, STDIN, STDOUT and STDERR.
    * \> – save output to a file.
    * \>> – append output to a file.
    * < – read input from a file.
    * 2> – redirect error messages.
    * | – send the output from one program as input to another program.
* Control
    * We have quite a bit of control over the running of our programs.
    * ctrl + z – pause the current foreground process and move it into the background
* Scripts behave the same
    * Anything you may do on the command line you may do in a script and it will behave exactly the same.
* Formatting
    * Bash scripts are particularly picky when it comes to formatting. Make sure spaces are put where they are needed and not put when they are not needed.
    * $ – Placed before a variable name when we are referring to its value.
    * \`` – Backticks. Used to save the output of a program into a variable.
* if [ ] then else fi – Perform basic conditional logic.
    * if - Perform a set of commands if a test is true.
    * else - If the test is not true then perform a different set of commands.
    * elif - If the previous test returned false then try this one.
    * && - Perform the and operation.
    * || - Perform the or operation.

* while
```bash
while [ condition ]
do
    command1
    command2
    command3
done
``` 

***

#### The best way to analyze a command run

\>& - save the output of the command into a file
Ex: `make counter_arty >& counter_arty.log`

control+z to stop the run

`bg` to have the command keep running in the background

`jobs` shows what is running in the background

`tail -f counter_arty.log &` or other filename to see the final lines as it runs.

----------------------------------
Initially created by Ryan Johnson, June 2020.