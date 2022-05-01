# Java-Interview-Questions-And-Answers
Collection of most important real time java interview question and answers.

1- What's the difference between Thread start() and Runnable run() ?


## Collection Interview Questions.
1.	What is the difference between collection and collections?
```

Collection : A collection (also called as container) is an object  that groups multiple elements into a single unit.

Collections Framework : Collections framework provides unified architecture for manipulating and representing collections.

Benefits of Collections Framework :

1. Improves program quality and speed
2. Increases the chances of reusability of software
3. Decreases programming effort.



Collection is  an interface while Collections is a java class , both are present in java.util package and  part of java collections framework.

```

2. What is difference between array list vs linked list?
```
1) Search: ArrayList search operation is pretty fast compared to the LinkedList search operation. get(int index) in ArrayList gives the performance of O(1) while LinkedList performance is O(n).

Reason: ArrayList maintains index based system for its elements as it uses array data structure implicitly which makes it faster for searching an element in the list. On the other side LinkedList implements doubly linked list which requires the traversal through all the elements for searching an element.

2) Deletion: LinkedList remove operation gives O(1) performance while ArrayList gives variable performance: O(n) in worst case (while removing first element) and O(1) in best case (While removing last element).


Reason: LinkedList’s each element maintains two pointers (addresses) which points to the both neighbor elements in the list. Hence removal only requires change in the pointer location in the two neighbor nodes (elements) of the node which is going to be removed. While In ArrayList all the elements need to be shifted to fill out the space created by removed element.

3) Inserts Performance: LinkedList add method gives O(1) performance while ArrayList gives O(n) in worst case. Reason is same as explained for remove.

4) Memory Overhead: ArrayList maintains indexes and element data while LinkedList maintains element data and two pointers for neighbor nodes hence the memory consumption is high in LinkedList comparatively.

There are few similarities between these classes which are as follows:

Both ArrayList and LinkedList are implementation of List interface.
They both maintain the elements insertion order which means while displaying ArrayList and LinkedList elements the result set would be having the same order in which the elements got inserted into the List.
Both these classes are non-synchronized and can be made synchronized explicitly by using Collections.synchronizedList method.
The iterator and listIterator returned by these classes are fail-fast (if list is structurally modified at any time after the iterator is created, in any way except through the iterator’s own remove or add methods, the iterator will throw a ConcurrentModificationException).
When to use LinkedList and when to use ArrayList?
1) As explained above the insert and remove operations give good performance (O(1)) in LinkedList compared to ArrayList(O(n)). Hence if there is a requirement of frequent addition and deletion in application then LinkedList is a best choice.

2) Search (get method) operations are fast in Arraylist (O(1)) but not in LinkedList (O(n)) so If there are less add and remove operations and more search operations requirement, ArrayList would be your best bet.

```

3. What is difference between array vs arraylist?

```
Array is used to hold multiple values of same type. An array may hold -

multiple primitive values of same type , or
multiple object references of same type.
Types of array -

One-dimensional array(1-D), it's a single array that holds multiple values of the same type. For more on Array , you may read, Array in Java- Decodejava.com
Two-dimensional array(2-D), it's an array containing multiple arrays within it, where all of these multiple array holding values of a same type. For more on 2D array and how they are declared, initialized and created, you may read Two Dimensional Array in Java
ArrayList : Just like a standard array, ArrayList is also used to store similar elements. In the case of a standard array, we must declare its size before we use it and once its size is declared, it's fixed. While ArrayList is like a dynamic array i.e. we don't need to declare its size, it grows as we add elements to it and it shrinks as you remove elements from it, during the runtime of the program.
```
4. What is comparable vs comparator? (Explain with program)

```
Comparable vs Comparator in Java
Java provides two interfaces to sort objects using data members of the class:

Comparable
Comparator
Using Comparable Interface

A comparable object is capable of comparing itself with another object. The class itself must implements the java.lang.Comparable interface to compare its instances.

Consider a Movie class that has members like, rating, name, year. Suppose we wish to sort a list of Movies based on year of release. We can implement the Comparable interface with the Movie class, and we override the method compareTo() of Comparable interface.



 

filter_none
edit
play_arrow

brightness_4
// A Java program to demonstrate use of Comparable 
import java.io.*; 
import java.util.*; 
  
// A class 'Movie' that implements Comparable 
class Movie implements Comparable<Movie> 
{ 
    private double rating; 
    private String name; 
    private int year; 
  
    // Used to sort movies by year 
    public int compareTo(Movie m) 
    { 
        return this.year - m.year; 
    } 
  
    // Constructor 
    public Movie(String nm, double rt, int yr) 
    { 
        this.name = nm; 
        this.rating = rt; 
        this.year = yr; 
    } 
  
    // Getter methods for accessing private data 
    public double getRating() { return rating; } 
    public String getName()   {  return name; } 
    public int getYear()      {  return year;  } 
} 
  
// Driver class 
class Main 
{ 
    public static void main(String[] args) 
    { 
        ArrayList<Movie> list = new ArrayList<Movie>(); 
        list.add(new Movie("Force Awakens", 8.3, 2015)); 
        list.add(new Movie("Star Wars", 8.7, 1977)); 
        list.add(new Movie("Empire Strikes Back", 8.8, 1980)); 
        list.add(new Movie("Return of the Jedi", 8.4, 1983)); 
  
        Collections.sort(list); 
  
        System.out.println("Movies after sorting : "); 
        for (Movie movie: list) 
        { 
            System.out.println(movie.getName() + " " + 
                               movie.getRating() + " " + 
                               movie.getYear()); 
        } 
    } 
} 
Output:

Movies after sorting : 
Star Wars 8.7 1977
Empire Strikes Back 8.8 1980
Return of the Jedi 8.4 1983
Force Awakens 8.3 2015
Now, suppose we want sort movies by their rating and names also. When we make a collection element comparable(by having it implement Comparable), we get only one chance to implement the compareTo() method. The solution is using Comparator.

 

Using Comparator

Unlike Comparable, Comparator is external to the element type we are comparing. It’s a separate class. We create multiple separate classes (that implement Comparator) to compare by different members.

Collections class has a second sort() method and it takes Comparator. The sort() method invokes the compare() to sort objects.

To compare movies by Rating, we need to do 3 things :

Create a class that implements Comparator (and thus the compare() method that does the work previously done by compareTo()).
Make an instance of the Comparator class.
Call the overloaded sort() method, giving it both the list and the instance of the class that implements Comparator.
filter_none
edit
play_arrow

brightness_4
//A Java program to demonstrate Comparator interface 
import java.io.*; 
import java.util.*; 
  
// A class 'Movie' that implements Comparable 
class Movie implements Comparable<Movie> 
{ 
    private double rating; 
    private String name; 
    private int year; 
  
    // Used to sort movies by year 
    public int compareTo(Movie m) 
    { 
        return this.year - m.year; 
    } 
  
    // Constructor 
    public Movie(String nm, double rt, int yr) 
    { 
        this.name = nm; 
        this.rating = rt; 
        this.year = yr; 
    } 
  
    // Getter methods for accessing private data 
    public double getRating() { return rating; } 
    public String getName()   {  return name; } 
    public int getYear()      {  return year;  } 
} 
  
// Class to compare Movies by ratings 
class RatingCompare implements Comparator<Movie> 
{ 
    public int compare(Movie m1, Movie m2) 
    { 
        if (m1.getRating() < m2.getRating()) return -1; 
        if (m1.getRating() > m2.getRating()) return 1; 
        else return 0; 
    } 
} 
  
// Class to compare Movies by name 
class NameCompare implements Comparator<Movie> 
{ 
    public int compare(Movie m1, Movie m2) 
    { 
        return m1.getName().compareTo(m2.getName()); 
    } 
} 
  
// Driver class 
class Main 
{ 
    public static void main(String[] args) 
    { 
        ArrayList<Movie> list = new ArrayList<Movie>(); 
        list.add(new Movie("Force Awakens", 8.3, 2015)); 
        list.add(new Movie("Star Wars", 8.7, 1977)); 
        list.add(new Movie("Empire Strikes Back", 8.8, 1980)); 
        list.add(new Movie("Return of the Jedi", 8.4, 1983)); 
  
        // Sort by rating : (1) Create an object of ratingCompare 
        //                  (2) Call Collections.sort 
        //                  (3) Print Sorted list 
        System.out.println("Sorted by rating"); 
        RatingCompare ratingCompare = new RatingCompare(); 
        Collections.sort(list, ratingCompare); 
        for (Movie movie: list) 
            System.out.println(movie.getRating() + " " + 
                               movie.getName() + " " + 
                               movie.getYear()); 
  
  
        // Call overloaded sort method with RatingCompare 
        // (Same three steps as above) 
        System.out.println("\nSorted by name"); 
        NameCompare nameCompare = new NameCompare(); 
        Collections.sort(list, nameCompare); 
        for (Movie movie: list) 
            System.out.println(movie.getName() + " " + 
                               movie.getRating() + " " + 
                               movie.getYear()); 
  
        // Uses Comparable to sort by year 
        System.out.println("\nSorted by year"); 
        Collections.sort(list); 
        for (Movie movie: list) 
            System.out.println(movie.getYear() + " " + 
                               movie.getRating() + " " + 
                               movie.getName()+" "); 
    } 
}   
Output :

Sorted by rating
8.3 Force Awakens 2015
8.4 Return of the Jedi 1983
8.7 Star Wars 1977
8.8 Empire Strikes Back 1980

Sorted by name
Empire Strikes Back 8.8 1980
Force Awakens 8.3 2015
Return of the Jedi 8.4 1983
Star Wars 8.7 1977

Sorted by year
1977 8.7 Star Wars 
1980 8.8 Empire Strikes Back 
1983 8.4 Return of the Jedi 
2015 8.3 Force Awakens  
Comparable is meant for objects with natural ordering which means the object itself must know how it is to be ordered. For example Roll Numbers of students. Whereas, Comparator interface sorting is done through a separate class.
Logically, Comparable interface compares “this” reference with the object specified and Comparator in Java compares two different class objects provided.
If any class implements Comparable interface in Java then collection of that object either List or Array can be sorted automatically by using Collections.sort() or Arrays.sort() method and objects will be sorted based on there natural order defined by CompareTo method.
```
5. What is hash set and how hashset internally works?
6. Difference between HashSet , LinkedHashSet and TreeSet?
7. How HashSet ensure unique ness?
8. What is contract between hashcode() and equals() methods?
9. What is HashMap and how hashmap internally works.
10. What is difference between HashMap, LinkedHashMap and TreeMap?
11. What is different between Concurrent HashMap and Synchronized version of hash Map?
12. What is iterator, list iterator and enumerator?
13. What is the use of Copy on Write Arraylist?
14. Calculate number of Duplicates in Array list?
15. What is the meaning of ThreadLocal?
```
The ThreadLocal class is used to create thread local variables which can only be read and written by the same thread. 
For example, if two threads are accessing code having reference to same threadLocal variable then each thread will not see any 
modification to threadLocal variable done by other thread.

```
16. what is volatile keyword in java
```
The volatile field is needed to make sure that multiple threads always see the newest value, 
even when the cache system or compiler optimizations are at work. 
Reading from a volatile variable always returns the latest written value from this variable.

```

17. Spring boot setup global exception handler.
```

@ControllerAdvice
public class CustomizedExceptionHandling extends ResponseEntityExceptionHandler {

    @ExceptionHandler(TeacherNotFoundException.class)
    public ResponseEntity<Object> handleExceptions( TeacherNotFoundException exception, WebRequest webRequest) {
        ExceptionResponse response = new ExceptionResponse();
        response.setDateTime(LocalDateTime.now());
        response.setMessage("Not found");
        ResponseEntity<Object> entity = new ResponseEntity<>(response,HttpStatus.NOT_FOUND);
        return entity;
    }
}
```
18. What is volatile and transient keyword in Java?
```
The volatile keyword flushes the changes directly to the main memory instead of the CPU cache. On the other hand, 
the transient keyword is used during serialization.

```
