## Phone interview preparation

#### Predicted questions

1.  Explain 4 major principles that mane OOP [link](https://medium.com/@cancerian0684/what-are-four-basic-principles-of-object-oriented-programming-645af8b43727)

    -   Data abstraction

        > objects in an OOP language provide an abstraction that hides the internal implementation details

    -   Encapsulation

        > is a mechanism of hiding the data and making it accessable by setters and getters

    -   Pylomorphism

        > means one name, many forms. occurs when we have many classes that are related to each other by inheritance
        > Example: we have animal classes like Dog, Pig and Animal class itself. `Animal myPig = new Pig();` is valid. We can use this to store different animals in a list for example

    -   Inheritance

        > expresses “is-a” and/or “has-a” relationship between two objects (class X extends Y =java=)

2.  Generics in Java [link](https://www.tutorialspoint.com/java/java_generics.htm)

    > Allows to write a single function for different types of arguments. Example: List<>, Dictionary<>, Sort<>, Print<>

3.  Big O complexity
    > Big O notation characterizes functions according to their growth
4.  Find algorithms
    -   Linear
    -   Binary (has to be presorted)
    -   Jump (jump unless find smaller value, get back end do linear, has to be presorted)
5.  Sort algorigthms

    -   Selection sort
        Iterate, find smallest(or biggest), add to new array, pop old value
    -   Bubble sort
        Iterate array multiple times and swap neighbors if needed
    -   Insertion sort
        Works as sorting cards in hands. Pulling back untill its smaller(bigger)
    -   Merge sort
        Splitting recursively in half and swapping when we have 2 elems, then joining 2 recursive functions (n and n - 1)
    -   Quick sort

    -   Heap sort - using complete binary tree. Forming min/max heap. Difficult to implement. O=nlogn complexity

6.  Difference final, finally and finalize in Java

    -   final means that it wont change (like variable, or if cass then methods only)
    -   finally is used with try/catch
    -   finalize class method is called after deconstructor to do garbage collection

7.  Software design
8.  Operating systems
9.  Database design
    -   Normalization forms
