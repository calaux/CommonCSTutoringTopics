## How to Use `gprolog` ##

This should work with `gprolog` on the CSIF computers.

### Starting `gprolog` ###

From a terminal window, type the command `gprolog`.

    [calaux@pc24 hw6]$ gprolog
    GNU Prolog 1.4.4 (32 bits)
    Compiled Sep 26 2014, 18:27:29 with gcc
    By Daniel Diaz
    Copyright (C) 1999-2013 Daniel Diaz
    | ?-

### Loading Your Code and Running Programs ###

There are a couple of ways to load your files into `gprolog`:

- Put brackets around the path to your file, with single quotations around the name. (And don't forget the period.)

    	| ?- ['sched.pl'].
    	compiling /home/calaux/140A/hw6/HW6/sched.pl for byte code...
    	/home/calaux/140A/hw6/HW6/sched.pl compiled, 186 lines read - 19617 bytes written, 29 ms
    
    	(5 ms) yes
    	| ?-

- Call the consult function, with single quotation marks around the path to your file. (Remember the period!)

		| ?- consult('sched.pl').
		compiling /home/calaux/140A/hw6/HW6/sched.pl for byte code...
		/home/calaux/140A/hw6/HW6/sched.pl compiled, 186 lines read - 19617 bytes written, 15 ms

		(5 ms) yes
		| ?-

If you need to reload a file, use `reconsult` instead.

Now you can run queries defined in your files. 

### Exiting `gprolog` ###

There are a couple of methods to exit `gprolog`:

- Type in the command `halt`, followed by a period.

		| ?- halt.
		[calaux@pc24 HW6]$

- Press `CTRL-D` (EOF) on your keyboard.
