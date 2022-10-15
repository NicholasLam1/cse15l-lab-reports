# Lab Report 2 

## Part 1 

Below is my code for SearchEngine.java. It uses Arraylists for its data structures. 
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
Here are the results of adding "pineapple" and "apple", and then searching for "app".

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic1.png)
![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic2.png)
![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic3.png)

The methods that are called when /add?=pineapple is the input are getQuery(), split(), equals(), and add(). These methods together read the query and extracts the string to be added and then adds it to a list that keeps track of all of the strings. The relevant argument in split() is "=" and for equals() is "s". If parameters[0] is equal to "s", then it is added to the list by list.add() with parameters[1] as its argument. The value of parameters[1] can vary. As seen in the second screenshot, when /add?=apple is the input, all the same methods as before are called. The only difference is that the value of parameters[1] is now apple instead of pineapple. Also, since pineapple was added first, apple would be the second element in the list. The methods that are called when /search?s=app is the input are getQuery(), split(), equals(), size(), indexOf(), add(), and get(). These methods together read the substring to be searched and then goes through the list of existing strings and returns which strings have that exact substring. The getQuery(), split(), and equals() method have the same arguments when adding a string. The size method is used to get the size of the list in order to transverse it. In the for loop, get(i) refers to the i-th element in the list and indexOf() is used to see if the element in the list has the substring and the relevant argument is parameters[1]. If the string does contain the substring it is added to another list called match using add() with list.get(i) as the argument. parameters[1] can vary and corresponds to the different substring that is being searched for within the strings. 

## Part 2

The screenshot below shows a failure-inducing input 
and the symptom for the bug in the averageWithoutLowest() method in the ArrayExamples.java file.

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic4.png)

The input of an array of type double which was has an average of 2.0 when excluding the lowest value has the symptom of returning the wrong average of 1.667.

```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      { sum += num; }
    }
    sum = sum - lowest;
    return sum / (arr.length - 1);
  }
}
```

The code above fixes the bug. The reason the bug caused that specific symptom is because the input had the lowest value twice in the array. The program would add all the values in the array that were not the lowest which works fine if there is only one lowest value. The failure inducing input had two 1.0 values and instead of only one, both of them were not added into the sum. My fix adds all the elements in the array and then subtracts the lowest value from the sum to remove only a singular lowest value. 



The screenshot below shows a failure-inducing input 
and the symptom for the bug in the filter() method in the ListExamples.java file.

![Image](https://raw.githubusercontent.com/NicholasLam1/cse15l-lab-reports/main/lab2pic5.png)

The input of an List with values of "abc", "abcd", and "abcdefghi" when gone through the filter method has the  symptom of returning the wrong order of the expected output. The filter should allow only strings less than 5 characters to pass, so the order of the output should be abc then abcd, the it was actual abcd then abc. 

```
static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
```

The code above fixes the bug. The reason the bug caused that specific symptom is because the strings were added to the 0th position of the list. In other words, after checking the strings, the method would add the string to the beginning of the list which inadvertently reversed the order. My fix changes the way the strings are added so that it adds to the end of the list. This perseveres the order of the original list. 
