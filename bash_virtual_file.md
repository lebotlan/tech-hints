Consider `command1 <(command2)`

`<(command2)` creates a fifo, returns a virtual file (it returns a file name)

Useful when:

 - command1 does not read stdin but expects only a file name.
 - command1 expects several arguments, which you want to replace by the output of some other commands.

Note :

 - it is a fifo, not a file (the content can only be processed once)


