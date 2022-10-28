# Week 3 Lab Report

**Assignment:** Instructions [here](https://ucsd-cse15l-f22.github.io/week/week3/).

---

### **Part 1:** Simplest Search Engine

Code:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

//Credit: copied template from NumberServer.java
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> searches = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            String allsearches = new String();
            for (int i = 0; i < searches.size(); i++) {
                allsearches += searches.get(i) + "\n";
            }
            return allsearches;
        } else if (url.getPath().equals("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                searches.add(parameters[1]);
                return "Search [" + parameters[1] + "] was added!";
            }
        } else if (url.getPath().contains("/search")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                String allsearches = new String();
                String query = parameters[1];
                for (int i = 0; i < searches.size(); i++) {
                    if (searches.get(i).contains(query)) {
                        allsearches += searches.get(i) + "\n";
                    }
                }
                return allsearches;
            }
        }
        return "404 Not Found!";
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

**Screenshot 1.** Add

* Method: handleRequest
* Relevant Argument: URI url (in this case, https://localhost:4141/add?s=anewstringtoadd, which when gets parsed so we can see the key word "add" and process it accordingly)
* Relevant Value: getPath ("/add", for adding a word to the search), getQuery ("s", for indicating the search word, "[word]", for inputting the word to add)
* Values: Array storing all searches gets the new word (anewstringtoadd) added to it, going from empty to size 1

<img width="316" alt="image" src="https://user-images.githubusercontent.com/44093048/195966964-c965c462-9894-4a19-be18-71c10b16f139.png">

**Screenshot 2.** Search

* Method: handleRequest
* Relevant Argument: URI url (in this case, https://localhost:4141/search?s=app)
* Relevant Value: getPath ("/search", for indicating you want to search in past words), getQuery ("s", for indicating the search word, "[word]", for inputting the word/letters to search each previous recorded word for)
* Values: do not change during function

<img width="263" alt="image" src="https://user-images.githubusercontent.com/44093048/195966991-c3c711d4-0be9-4bd8-a321-a37ad2b71afb.png">


**Screenshot 3.** Show Past Searches

* Method: handleRequest
* Relevant Argument: URI url (in this case, https://localhost:4141/)
* Relevant Value: getPath ("/", the home page that prints all prior added words)
* Values: do not change during function

<img width="205" alt="image" src="https://user-images.githubusercontent.com/44093048/195967010-839a28e1-7ed4-4493-88a0-aaa044b2166a.png">


### **Part 2:** Bugs in Files 

**Bug 1.** Array's Reversed() Function

_Failure-inducing input:_ 

<img width="466" alt="image" src="https://user-images.githubusercontent.com/44093048/195967685-1b51165f-3516-464f-a567-43c414b17559.png">

_Symptom:_ The answer array contains 0s instead of the expected values of the flipped array.

<img width="465" alt="image" src="https://user-images.githubusercontent.com/44093048/195967711-99ccfb3b-b220-4a9c-98bb-0e6defce837f.png">

_Bug:_ newArray and arr (original array) are swapped around in the code. Instead of the values from arr being assigned to newArray in a flipped order, the code is assigning
the empty newArray's values (i.e. all 0s) to the original array, and then returning the now empty (full of 0s) arr.

_Fixed code:_ Swapped the positions of newArray and arr in the code so that arr’s values are being assigned to newArray (instead of vice versa) and newArray is returned.

<img width="467" alt="image" src="https://user-images.githubusercontent.com/44093048/195967720-a5918d2a-e012-41d4-8cd7-1c29bb48334d.png">

_Connections:_ This bug causes this particular symptom in any test case where the input array contains at least one number. It's impossible to tell with an empty array input 
or an array full of zeros (as getting an empty array or an array full of zeros would be correct in this case), but with non-zero numbers in the array, 
it becomes obvious that instead of [5,6] flipping to become [6,5], the function is outputting [0,0] instead - aka the array has been changed back into an empty, 
newly initialized array.

**Bug 2.** List's Filter() Function

_Failure-inducing input:_ 

<img width="271" alt="image" src="https://user-images.githubusercontent.com/44093048/195967289-52f530c0-c014-4ebb-b460-90742c6aff9c.png">

_Symptom:_ The answer list contains all the correct strings, but the order they should be in are flipped. 

<img width="467" alt="image" src="https://user-images.githubusercontent.com/44093048/195967313-f963aac3-898d-4189-9495-7a14efbae7bf.png">

_Bug:_ The function keeps adding good strings (strings that fulfill the requirement) to the 0 index, i.e. whole answer list is in reversed order

_Fixed code:_ Removed the "0" in ".add(0, s)" so that each new good string processed is added to the end of the answer array, not at the beginning. 

<img width="274" alt="image" src="https://user-images.githubusercontent.com/44093048/195967344-fd05f874-68c8-4fb3-ac80-eaa0776f3740.png">

_Connections:_ This bug causes this particular symptom in any test case where the answer array contains 2+ strings, which includes this particular input (where the answer array contains
two strings, ["alrighty", "yepyep"]). This is because it puts all the strings into the array in reverse order (by adding each new one to the beginning of the array, though
each new one processed is behind the one before it in the order). If the answer array only contained 1 string, or none at all, then this symptom would not show up because the array
would be in the same order no matter which way it was read.


