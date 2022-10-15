# Lab Report 2 

## Part 1 

Below is the code for the SearchEngine.java. It uses Arraylists for its data strucutre. 
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
 
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    ArrayList<String> list = new ArrayList<String>();
    ArrayList<String> match = new ArrayList<String>();
 
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format("Number: %d", num);
        } else if (url.getPath().equals("/search")) {
            String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    for (int i=0; i<list.size(); i++){
                        if (list.get(i).indexOf(parameters[1]) != -1) {
                            match.add(list.get(i));
                        }
                    }
                    String s = "Matches: ";
                    for (int i=0; i<match.size(); i++){
                        s = s + " " + String.format(match.get(i));
                    }
                    return s;
                }            
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    list.add(parameters[1]);
                }
                return String.format("Done: added %s", parameters[1]);
            }
            return "404 Not Found!";
        }return String.format("Done");
    }
}
 
class SearchEngine {
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
Here are the result of adding "pineapple" and "apple", and then searching for "app".

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic1.png)
![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic2.png)
![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic3.png)

The methods that are called when /add?=pinapple is the input are getQuery(), split(), equals(), and add(). These methods together read the queary and extracts the string to be add and then adds it to a list that keeps track of all of the strings. The relevant argument in split() is "=" and for equals() is "s". If parameters[0] is equal to "s", then it is added to the list by list.add() with parameters[1] as its argument. The value of parameters[1] can vary. As seen in the second screenshot, when /add?=apple is the input, all the same methods as before are called. The only difference is that the value of parameters[1] is now apple instead of pineapple. Also since pinapple was added first, apple would be the second element in the list. The methods that are called when /search?s=app is the input are getQuery(), split(), equals(), size(), indexOf(), add(), and get(). These methods together read the substring to be searhced and then goes through the list of existing strings and returns which strings have that exact substring. The getQuery(), split(), and equals() method have the same arguments when adding a string. The size method is used to get the size of the list in order to transverse it. In the for loop, get(i) refers to the ith element in the list and indexOf() is used to see if the element in the list has the substring and the relevant arguemtn is parameters[1]. If the string does contain the substring it is added to another list called match using add() with list.get(i) as the arugment. parameters[1] can vary and corresponf the diferent substring that is being serached for within the strings. 

## Part 2