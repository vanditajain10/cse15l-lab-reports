# CSE 15 L WEEK 2 LAB REPORT 

## PART 1 

* Code for the Chat Server

```import java.io.IOException;
import java.net.URI;


class Handler implements URLHandler {

   String displayMssg="";
    
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return "Start adding your Strings";
        }
        else{
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    String[] subParameter=(parameters[1]).split("&");
                    displayMssg+=parameters[2]+": "+ subParameter[0]+"\n";
                    return displayMssg;
                    
                    }
                
                }
            return "404 Not Found";
        
        }
    }
        
}


class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
} ```
