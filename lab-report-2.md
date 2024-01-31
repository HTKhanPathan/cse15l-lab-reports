# Part 1 of the report
## chatserver code
```
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
