## How to Use CLISP ##

This should work with CLISP on the CSIF computers.

### Starting CLISP ###

From a terminal window, type the command `clisp`.

    [calaux@pc24 hw5]$ clisp
	/* There was a pretty picture of the CLISP logo, but Markdown didn't like it... :( */
    Welcome to GNU CLISP 2.49+ (2010-07-17) <http://clisp.org/>
    
    Copyright (c) Bruno Haible, Michael Stoll 1992, 1993
    Copyright (c) Bruno Haible, Marcus Daniels 1994-1997
    Copyright (c) Bruno Haible, Pierpaolo Bernardi, Sam Steingold 1998
    Copyright (c) Bruno Haible, Sam Steingold 1999-2000
    Copyright (c) Sam Steingold, Bruno Haible 2001-2010
    
    Type :h and hit Enter for context help.
    
    [1]>

### Loading Your Code and Running Programs ###

At the command prompt, call the `load` function. (Yes, you have to put parentheses around this.) With the parameter, provide the path of your file in double quotation marks.

`[1]> (load "test.l")`

Run your program by calling whatever functions you defined, with appropriate parameters.

### Debugging ###

If there is an error in your program or you mistype a command, the debugger gets invoked. Unless you want to use the debugger, type `:q` so that you are not running your programs with the debugger.

#### Example ####
    [4]> (hello)
    
    *** - EVAL: undefined function HELLO
    The following restarts are available:
    USE-VALUE  		:R1  	Input a value to be used instead of (FDEFINITION 'HELLO).
    RETRY  			:R2  	Retry
    STORE-VALUE		:R3  	Input a new value for (FDEFINITION 'HELLO).
    ABORT  			:R4  	Abort main loop
    Break 1 [5]> :q
	[6]>

### Exiting CLISP ###

There are numerous ways of ending your CLISP session, listed below. (Once again, parentheses are necessary...)

- `(exit)`
- `(bye)`
- `(quit)`

CLISP for some reason says bye to you, too.