# Testing cd commands
## Testing cd with a directory
```
[user@sahara ~]$ cd lecture1 
[user@sahara ~/lecture1]$
```
## Testing cd with no argument
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$\
```
## Testing cd with a file
```
[user@sahara ~]$ cd lecture1/messages/en-us.txt
 bash: cd: lecture1/messages/en-us.txt: Not a directory
```
# Testing ls commands
## Testing ls with no argument
```
[user@sahara ~]$ ls
lecture1
```
## Testing ls with a directory
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
## Testing ls with a file
```
[user@sahara ~]$ ls lecture1/messages/en-us.txt 
lecture1/messages/en-us.txt
```
# Testing cat commands
## Testing cat with no argument
```
[user@sahara ~]$ cat

```
It completely eliminates the terminal prompt and makes the terminal unusable for someone at my level
## Testing cat with a directory
```
[user@sahara ~]$ cat lecture1/
cat: lecture1/: Is a directory
```
## Testing cat with a file
```
[user@sahara ~]$ cat lecture1/messages/en-us.txt lecture1/messages/ur-pk.txt 
Hello World!
Salam Duniya!
```
