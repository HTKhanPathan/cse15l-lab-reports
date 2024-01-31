# Part 1 of the report
## chatserver code
```java
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler{
    public String handleRequest(URI url){
        if (url.getPath() == null){
            return msgString;
        }
        if (url.getPath().contains("/add")) {
            String[] ampers = url.getQuery().split("&");
            String[] beforeAmper = ampers[0].split("=");
            String[] postAmper = ampers[1].split("=");
            msgString += String.format("%s: %s \n",postAmper[1],beforeAmper[1]);
            return msgString;
        } else {
            return "404";
        }
    }
    String msgString = "";
}
class chatserver{
    public static void main(String[] args) throws IOException{
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
## screenshots of using /add
![Image](https://github.com/HTKhanPathan/cse15l-lab-reports/blob/main/screenshot%20of%20using%20%3Aadd%20message%20for%20the%20first%20time.png)
The `main` method is called with the port as the argument. After that the Server is started and with the /add included to the url the `handleRequest` method is called with the url as the argument. \
If `url.getPath()` contains the `/add` keyword, it will create three string arrays: `ampers` which includes everything after the `?` and splits at the `&` \
`beforeAmper` includes what comes before the `&` and `postAmper` includes what comes after the `&`  both split at the `=` \ `msgString` is initialized with an empty string. \
With this specific url `/add-message?s=Hello&user=jpolitz` ampers has two values `ampers[0]` = `s=Hello` and `ampers[1]` = `user=jpolitz` \
`beforeAmper[1]` = `Hello` and `postAmper[1]` = `jpolitz` and finally `msgString` = `jpolitz: Hello` with a new line starting at the end


## screenshot of using /add for the second time
![Image](https://github.com/HTKhanPathan/cse15l-lab-reports/blob/main/screen%20shot%20of%20using%20add%20message%20second%20time.png?raw=true)
The `main` method is called which in turn calls `handleRequest` method with the url as the argument. \
If `url.getPath()` contains the `/add` keyword, it will create once again three string arrays: `ampers` which includes everything after the `?` and splits at the `&` \
`beforeAmper` includes what comes before the `&` and `postAmper` includes what comes after the `&`  both split at the `=` \ `msgString` is `jpolitz: Hello`  \
With this specific url `/add-message?s=How are you&user=h4khan` ampers has two values `ampers[0]` = `s=How are you` and `ampers[1]` = `user=h4khan` \
`beforeAmper[1]` = `How are you` and `postAmper[1]` = `h4khan` and finally `msgString` = `jpolitz: Hello \n h4khan: How are you`  with the \n representing a new line starting. \
This updated value of the msgString is the previous value with the new string appended to it. All other values got changed with new arguments while msgString got appended.

# Part 2 of the lab report
## screenshot of ieng6 login requiring no password:
![Image](https://github.com/HTKhanPathan/cse15l-lab-reports/blob/main/screenshot%20of%20ieng6%20with%20no%20pass.png)


# part 3
A new thing I learnt in this weeks lab was using mkdir and scp and also creating a chat server. It really gave me a new insight on how websites work and what goes on behind the screen.\
I also really liked working on the chat server and seeing the changes in real time.
