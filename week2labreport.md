# CSE 15 L WEEK 2 LAB REPORT 

## PART 1 

* Code for the ```ChatServer```

```

import java.io.IOException;
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
}

```
* Screenshots of using the ```/add-message```
  
* *Screenshot 1:*
 ![Image](add1.png)
1. The method in our code which are being called are ```handleRequest``` and the ```main``` method.
2.* The argument for the ```handleRequest``` is ``` URI url``` which is the the URL of the Server we have created. The specific fields which it uses is the ```displayMssg``` field which stores the final String to be displayed which has a current value of an empty string, ```parameters``` is a String array which is used to store the different parts of the query that we have passed in and ```subParameter``` is another String array which further stores the sub components of the query that are required to display the valid message. They both have current values as null.
* The argument for the ```main``` method is
3.* When we have passed this special request the the value of ```parameters``` becomes an array of
```["s","Love CSE 15 L&user","Vandita"]``` whereas the value of ```subParameter``` now becomes an array of ```["Love CSE 15 L","&","user"]``` and finally the value of the ```displayMssg``` field becomes the String ```Vandita: Love CSE 15 L \n``` which is what being displayed.
 * For the ```main``` method
    
* *Screenshot 2:*
![Image](add2.png)
1. The method in our code which are being called are ```handleRequest``` and the ```main``` method.
2.* The argument for the ```handleRequest``` is ``` URI url``` which is the the URL of the Server we have created. The specific fields which it uses is the ```displayMssg``` field which stores the final String to be displayed which has a current value of a String ```Vandita: Love CSE 15 L \n``` , ```parameters``` is a String array which is used to store the different parts of the query that we have passed in and ```subParameter``` is another String array which further stores the sub components of the query that are required to display the valid message. They both have current values as null.
* The argument for the ```main``` method is
3. * When we have passed this special request the the value of ```parameters``` becomes an array of ```["s","Bonjour&user","Shreya"]``` whereas the value of ```subParameter``` now becomes an array of ```["Bonjour","&","Shreya"]``` and finally the value of the ```displayMssg``` field becomes the String ```Vandita: Love CSE 15 L\n Shreya: Bonjour\n``` which is what being displayed.
 * For the ```main``` method

## PART 2
## PART 3
I learnt how to operate Servers as well as passing in query so that we can change what is being displayed and perform multiple actions in Week 2 . I was also fascinated by how we used the ```mkdir``` and ```ssh``` commands in Week 3 which actually enabled me to store my password. It was really unique to see that the terminal can only implement this and I didn't have to write much of java code too.
