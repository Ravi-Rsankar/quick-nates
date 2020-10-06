# Quick-notes: Python

#### Name some characteristics of Python?

- Python is an **interpreted language**. That means that, unlike languages like C and its variants, Python does not need to be compiled before it is run. Other interpreted languages include *PHP* and *Ruby*.
- Python is **dynamically typed**, this means that you don't need to state the types of variables when you declare them or anything like that. You can do things like `x=111` and then `x="I'm a string"` without error
- Python is well suited to **object orientated programming** in that it allows the definition of classes along with composition and inheritance. Python does not have access specifiers (like C++'s `public`, `private`), the justification for this point is given as "we are all adults here"
- In Python, **functions are first-class objects**. This means that they can be assigned to variables, returned from other functions and passed into functions. Classes are also first class objects
- Writing Python code is quick but running it is **often slower than compiled languages**. Fortunately, Python allows the inclusion of C based extensions so bottlenecks can be optimized away and often are. The `numpy` package is a good example of this, it's really quite quick because a lot of the number crunching it does isn't actually done by Python

#### Lists in Python

**Lists** are just like dynamic sized arrays. Lists need not be homogeneous always. A single list may contain DataTypes like Integers, Strings, as well as Objects. Lists are mutable, and hence, they can be altered even after their creation.

List in Python are ***ordered*** and have a definite count. The elements in a list are indexed according to a definite sequence and the indexing of a list is done with 0 being the first index. Each element in the list has its definite place in the list, which allows duplicating of elements in the list, with each element having its own distinct place and credibility.

##### insert()

`append()` method only works for addition of elements at the end of the List, for addition of element at the desired position, `insert() `method is used. Unlike `append()` which takes only one argument, `insert()` method requires two arguments(position, value).

##### extend()

Other than `append()` and `insert()` methods, there’s one more method for Addition of elements, `extend()`, this method is used to add multiple elements at the same time at the end of the list.

**Note –** [append() and extend()](https://www.geeksforgeeks.org/append-extend-python/) methods can only add elements at the end.

##### Negative indexing

In Python, negative sequence indexes represent positions from the end of the array. Instead of having to compute the offset as in `List[len(List)-3]`, it is enough to just write `List[-3]`. Negative indexing means beginning from the end, -1 refers to the last item, -2 refers to the second-last item, etc.

#### Sets in Python

A Set is an ***unordered*** collection data type that is iterable, mutable and has no duplicate elements. Python’s set class represents the mathematical notion of a set. The major advantage of using a set, as opposed to a list, is that it has a highly optimized method for checking whether a specific element is contained in the set. This is based on a data structure known as a [hash table](https://www.geeksforgeeks.org/hashing-set-1-introduction/). Since sets are unordered, we cannot access items using indexes like we do in [lists](https://www.geeksforgeeks.org/python-list/).