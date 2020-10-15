# Quick-notes: Python

### Name some characteristics of Python?

- Python is an **interpreted language**. That means that, unlike languages like C and its variants, Python does not need to be compiled before it is run. Other interpreted languages include *PHP* and *Ruby*.
- Python is **dynamically typed**, this means that you don't need to state the types of variables when you declare them or anything like that. You can do things like `x=111` and then `x="I'm a string"` without error
- Python is well suited to **object orientated programming** in that it allows the definition of classes along with composition and inheritance. Python does not have access specifiers (like C++'s `public`, `private`), the justification for this point is given as "we are all adults here"
- In Python, **functions are first-class objects**. This means that they can be assigned to variables, returned from other functions and passed into functions. Classes are also first class objects
- Writing Python code is quick but running it is **often slower than compiled languages**. Fortunately, Python allows the inclusion of C based extensions so bottlenecks can be optimized away and often are. The `numpy` package is a good example of this, it's really quite quick because a lot of the number crunching it does isn't actually done by Python

### Lists 

**Lists** are just like dynamic sized arrays. Lists need not be homogeneous always. A single list may contain DataTypes like Integers, Strings, as well as Objects. Lists are mutable, and hence, they can be altered even after their creation.

List in Python are ***ordered*** and have a definite count. The elements in a list are indexed according to a definite sequence and the indexing of a list is done with 0 being the first index. Each element in the list has its definite place in the list, which allows duplicating of elements in the list, with each element having its own distinct place and credibility.

##### insert()

`append()` method only works for addition of elements at the end of the List, for addition of element at the desired position, `insert() `method is used. Unlike `append()` which takes only one argument, `insert()` method requires two arguments(position, value).

##### extend()

Other than `append()` and `insert()` methods, there’s one more method for Addition of elements, `extend()`, this method is used to add multiple elements at the same time at the end of the list.

**Note –** [append() and extend()](https://www.geeksforgeeks.org/append-extend-python/) methods can only add elements at the end.

##### Negative indexing

In Python, negative sequence indexes represent positions from the end of the array. Instead of having to compute the offset as in `List[len(List)-3]`, it is enough to just write `List[-3]`. Negative indexing means beginning from the end, -1 refers to the last item, -2 refers to the second-last item, etc.

### Sets 

A Set is an ***unordered*** collection, sets do not record element position or order of insertion. Accordingly, sets do not support indexing, slicing, or other sequence-like behavior. 

They are mutable and has no duplicate elements. Python’s set class represents the mathematical notion of a set. 

The major advantage of using a set, as opposed to a list, is that it has a highly optimized method for checking whether a specific element is contained in the set. This is based on a data structure known as a [hash table](https://www.geeksforgeeks.org/hashing-set-1-introduction/). 

#### Implementation of Set

The set classes are implemented using dictionaries. Accordingly, the requirements for set elements are the same as those for dictionary keys; namely, that the element defines both [`__eq__()`](https://docs.python.org/2/reference/datamodel.html#object.__eq__) and [`__hash__()`](https://docs.python.org/2/reference/datamodel.html#object.__hash__). As a result, **sets cannot contain mutable elements** such as lists or dictionaries. However, they **can contain immutable collections** such as tuples or instances of [`ImmutableSet`](https://docs.python.org/2/library/sets.html#sets.ImmutableSet). For convenience in implementing sets of sets, inner sets are automatically converted to immutable form, for example, `Set([Set(['dog'])])` is transformed to `Set([ImmutableSet(['dog'])])`.

#### Operations in set

We can add a single element using the `add()` method, and multiple elements using the `update()` method. The `update()` method can take [tuples](https://www.programiz.com/python-programming/tuple), lists, [strings](https://www.programiz.com/python-programming/string) or other sets as its argument. In all cases, duplicates are avoided.

A particular item can be removed from a set using the methods `discard()` and `remove()`.

The only difference between the two is that the `discard()` function leaves a set unchanged if the element is not present in the set. On the other hand, the `remove()` function will raise an error in such a condition (if element is not present in the set).

### Ordered and Unordered collection

In python, list and tuples are ordered and dictionaries and sets are unordered.

In Lists and Tuples you will be able to access the elements based on their position. That is element at position 0 will always be at position 0 hence, can be accessed using integers like L[0] or T[0] and result will be the value in that index.

While in dictionary this cannot be done. The position of the elements may vary. So when you access elements in a dictionary, we don't do it based on position. we do it based on keys

### Tuple

In someways a tuple is similar to a list in terms of indexing, nested objects and repetition but a tuple is immutable unlike lists which are mutable.

### Dictionaries

