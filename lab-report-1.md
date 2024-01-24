# Testing cd commands
## Testing cd with a directory
```
[user@sahara ~]$ cd lecture1 
[user@sahara ~/lecture1]$
```
The cd command was run in the `/home` directory \
Not an error \
The command with a directory as an argument switches into that directory

## Testing cd with no argument
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$
```
The command was run in the `/lecture1` directory \
The command with no argument switches into the previous directory. If it is in a subdirectory like `/home/lecture1`, it will move into `/home`. \
Not an error
## Testing cd with a file
```
[user@sahara ~]$ cd lecture1/messages/en-us.txt
 bash: cd: lecture1/messages/en-us.txt: Not a directory
```
Command run in the `/home directory` \
Not an error \
The argument was a file name and it resulted in an error being thrown. The error was thrown because it could not find a directory with the name of the argument.
# Testing ls commands
## Testing ls with no argument
```
[user@sahara ~]$ ls
lecture1
```
When run in the `/home` directory, the ls command with no argument displays the immediate directory underneath it. In this case it is `/lecture1`. \
Not an error
## Testing ls with a directory
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
When the ls command is run in the `/home` directory with "lecture1" as the argument, it will display all the files and the directories inside the `/lecture1` directory. \
Not an error
## Testing ls with a file
```
[user@sahara ~]$ ls lecture1/messages/en-us.txt 
lecture1/messages/en-us.txt
```
When the ls command is run in the `/home` directory with a file name as the argument, it will repeat the name of the file. \
Not an error
# Testing cat commands
## Testing cat with no argument
```
[user@sahara ~]$ cat

```
When run in the `/home` directory with no argument, it will print out whatever is input into the terminal by the user. Basically \ 
it copies whatever is written in the terminal. This will run forever until ctrl+c is pressed. \
Not an error
## Testing cat with a directory
```
[user@sahara ~]$ cat lecture1/
cat: lecture1/: Is a directory
```
When the cat command is run in the `/home` directory with a directory name as the argument it produces an error becuase it cannot concatenate directories. \
Not an error
## Testing cat with a file
```
[user@sahara ~]$ cat lecture1/messages/en-us.txt lecture1/messages/ur-pk.txt 
Hello World!
Salam Duniya!
```
When run in the `/home` directory with the two file paths as the arguments, it concatenates and outputs the contents of both the files. \
Not an error
