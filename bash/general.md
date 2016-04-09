# Bash
(a.k.a. "Things applicable to practically all Bourne-derived shells")

Nearly everything covered here can be found in: http://linuxsig.org/files/bash_scripting.html

## Built-in Shell variables
(see: http://superuser.com/a/247131 as well as the [POSIX Standard](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_05_02))

```
$#    Stores the number of command-line arguments that 
      were passed to the shell program.
$?    Stores the exit value of the last command that was 
      executed.
$0    Stores the first word of the entered command (the 
      name of the shell program).
$*    Stores all the arguments that were entered on the
      command line ($1 $2 ...).
"$@"  Stores all the arguments that were entered
      on the command line, individually quoted ("$1" "$2" ...).
```
