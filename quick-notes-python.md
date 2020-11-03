# Quick-notes: Python

### Name some characteristics of Python?

- Python is an **interpreted language**. That means that, unlike languages like C and its variants, Python does not need to be compiled before it is run. Other interpreted languages include *PHP* and *Ruby*.
- Python is **dynamically typed**, this means that you don't need to state the types of variables when you declare them or anything like that. You can do things like `x=111` and then `x="I'm a string"` without error
- Python is well suited to **object orientated programming** in that it allows the definition of classes along with composition and inheritance. Python does not have access specifiers (like C++'s `public`, `private`), the justification for this point is given as "we are all adults here"
- In Python, **functions are first-class objects**. This means that they can be assigned to variables, returned from other functions and passed into functions. Classes are also first class objects
- Writing Python code is quick but running it is **often slower than compiled languages**. Fortunately, Python allows the inclusion of C based extensions so bottlenecks can be optimized away and often are. The `numpy` package is a good example of this, it's really quite quick because a lot of the number crunching it does isn't actually done by Python

### Attributes in Python

**Class Attributes**: Belong to the class itself. They will be shared by all the instances. All object refer to single copy

**Instance Attributes**:  Unlike class attributes, instance attributes are not shared by objects. Every object has its own copy of the instance attribute

### Abstract class

A class which contains one or more abstract methods is called an abstract class. 

An **abstract method** is a method that has a declaration but does not have an implementation. 

Abstract classes may not be instantiated, and its abstract methods must be implemented by its subclasses. 

When we want to provide a common interface for different implementations of a component, we use an abstract class.

#### Abstract base class

Python on its own doesn't provide abstract classes. Yet, Python comes with a module which provides the infrastructure for defining Abstract Base Classes (ABCs). 

```python
from abc import ABC, abstractmethod
 
class AbstractClassExample(ABC):
 
    def __init__(self, value):
        self.value = value
        super().__init__()
    
    @abstractmethod
    def do_something(self):
        pass
```

The above code creates an abstract class `AbstractClassExample` with an abstract method `do_something`. Which ever class inherits this abstract class has to implement the do_something method. Now we define two classes inheriting from our abstract class:

```python
class DoAdd42(AbstractClassExample):

    def do_something(self):
        return self.value + 42
    
class DoMul42(AbstractClassExample):
   
    def do_something(self):
        return self.value * 42
    
x = DoAdd42(10)
y = DoMul42(10)

print(x.do_something())
print(y.do_something())
52
420
```

A class that is derived from an abstract class cannot be instantiated unless all of its abstract methods are overridden.

You may think that abstract methods can't be implemented in the abstract base class. This impression is wrong: *An abstract method can have an implementation in the abstract class!* Even if they are implemented, designers of subclasses will be forced to override the implementation. Like in other cases of "normal" inheritance, the abstract method can be invoked with **super()** call mechanism. This enables providing some basic functionality in the abstract method, which can be enriched by the subclass implementation.

```python
from abc import ABC, abstractmethod
 
class AbstractClassExample(ABC):
    
    @abstractmethod
    def do_something(self):
        print("Some implementation!")
        
class AnotherSubclass(AbstractClassExample):

    def do_something(self):
        super().do_something()
        print("The enrichment from AnotherSubclass")
        
x = AnotherSubclass()
x.do_something()
        
Some implementation!
The enrichment from AnotherSubclass
```

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

#### Frozen Set

In Python, frozenset is same as set except its elements are immutable. This function takes input as any iterable object and converts them into immutable object. The order of element is not guaranteed to be preserved. 

Since frozenset object are immutable they are mainly used as key in dictionary or elements of other sets

### Ordered and Unordered collection

In python, list and tuples are ordered and dictionaries and sets are unordered.

In Lists and Tuples you will be able to access the elements based on their position. That is element at position 0 will always be at position 0 hence, can be accessed using integers like L[0] or T[0] and result will be the value in that index.

While in dictionary this cannot be done. The position of the elements may vary. So when you access elements in a dictionary, we don't do it based on position. we do it based on keys

### Tuple

Tuples are similar to list in terms of indexing. They are immutable lists which means that once a tuple is created you cannot delete or change the values of the items stored in it. You cannot add new values either. Tuples can hold both homogeneous as well as heterogeneous values. However, remember that once you declared those values, you cannot change them. Not only do they provide **"read-only"** access to the data values but **they are also faster than lists**.

### Dictionaries

- Mutable.
- Unordered.  it is not indexed by a sequence of numbers but indexed based on `keys`. a key cannot be a mutable data type. Keys are unique within a dictionary and can not be duplicated inside a dictionary, in case if it is used more than once then subsequent entries will overwrite the previous value. Key` connects with the `value
- To access the key value pair, you would use the `.items()` method, which will return a list of `dict_items` in the form of a key, value tuple pairs. To access keys and values separately, you could use a for loop on the dictionary or the `.keys()` and `.values()` method.
- Nesting is possible in dictionary. A value can be dictionary for a key.

#### Defaultdict

**Defaultdict** is a container like dictionaries present in the module **collections**. Defaultdict is a sub-class of the `dict` class that returns a dictionary-like object. The functionality of both dictionaries and defualtdict are almost same except for the fact that defualtdict never raises a `KeyError`. It provides a default value for the key that does not exists. The default value has to be defined on the creation of the dictionary. 

### Flask Vs Django

On the whole, both Flask and Django are widely used open source web frameworks for Python. Django is a full-stack web framework, whereas Flask is a micro and lightweight web framework. The features provided by Django help developers to build large and complex web applications. On the other hand, Flask accelerates development of simple web applications by providing the required functionality. Hence, the developers must keep in mind the needs of individual projects while comparing Flask and Django.

### What does immutable really mean

According to the official Python documentation, immutable is 'an object with a fixed value', but 'value' is a rather vague term, the correct term for tuples would be 'id'. 'id' is the identity of the location of an object in memory. The id will be different for different values of a variable. If the value is same then the location and hence the id will be same. Immutability is checked using this id.

Let's look a little more in-depth:

```python
# Tuple 'n_tuple' with a list as one of its item.
n_tuple = (1, 1, [3,4])

#Items with same value have the same id.
id(n_tuple[0]) == id(n_tuple[1])
True
#Items with different value have different id.
id(n_tuple[0]) == id(n_tuple[2])
False
id(n_tuple[0])
4297148528
id(n_tuple[2])
4359711048
n_tuple.append(5)
---------------------------------------------------------------------------

AttributeError                            Traceback (most recent call last)

<ipython-input-40-3cd258e024ff> in <module>()
----> 1 n_tuple.append(5)


AttributeError: 'tuple' object has no attribute 'append'
```

We cannot append item to a tuple, that is why you get an error above. This is why tuple is termed immutable. But, you can always do this:

```python
n_tuple[2].append(5)
n_tuple
(1, 1, [3, 4, 5])
```

Thus, allowing you to actually mutate the original tuple. How is the tuple still called immutable then?

This is because, the id of the list within the tuple still remains the same even though you appended 5 to it.

```python
id(n_tuple[2])
4359711048
```

### Data structure comparison 

**List**

- Lists are ordered.
- Lists can contain any arbitrary objects.
- List elements can be accessed by index.
- Lists can be nested to arbitrary depth.
- Lists are mutable.
- Lists are dynamic.

**Set**

- Sets are unordered
- Sets can contain any arbitrary objects.
- Its not index based.
- Does not allow duplicates.
- Sets are mutable, however only immutable objects are stored in it
- It has highly optimized methods to check where a element exists in it or not.

**Tuple**

- Tuples are ordered.
- Its immutable, read-only.
- Elements can be accessed through index, but they cannot be modified or deleted. However tuple allows to store mutable objects like list which can be modified
- It allows duplicate
- Since tuple is immutable, it requires a single block of memory and doesn't require extra space to store new objects. So *creating tuple is faster than list*. It also explains the slight difference in indexing speed is faster than lists,
  because in tuples for indexing it follows fewer pointers.
- Tuples can't be sorted

### Zip function

The purpose of zip() is to **map the similar index of multiple containers** so that they can be used just using as single entity. The function takes in [iterables](https://docs.python.org/3/glossary.html#term-iterable) as arguments and returns an **iterator**. This iterator generates a series of tuples. If you use `zip()` with `n` arguments, then the function will return an iterator that generates tuples of length `n`. 

```python
z = zip(['A', 'B', 'C'], [1,2,3])
set(z)
Output: {('A', 1), ('B', 2), ('C', 3)}
```

Unzipping means converting the zipped values back to the individual self as they were. This is done with the help of “*****” operator.

```python
z = zip(['A', 'B', 'C'], [1,2,3])
l = list(z)
l1, l2 = zip(*l)
print(l1)
print(l2)
Output: ('A', 'B', 'C')
		(1, 2, 3)
```

Python’s `zip()` function can take just one argument as well. The result will be an iterator that yields a series of 1-item tuples:

```python
a = [1, 2, 3]
zipped = zip(a)
list(zipped)
Output: [(1,), (2,), (3,)]
```

#### Passing arguments of unequal length

The number of elements that `zip()` puts out will be equal to the length of the *shortest* iterable. The remaining elements in any longer iterables will be totally ignored by `zip()`, as you can see here:

```python
list(zip(range(5), range(100)))
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4)]
```

#### Building dictionaries

```python
z = zip(['A', 'B', 'C'], [1,2,3])
d = dict(z)
print(d)
Output: {'A': 1, 'B': 2, 'C': 3}
```

### Built-in functions

#### all()

The all() method returns True when all elements in the given iterable are true. If not, it returns False.

```python
# all values true
l = [1, 3, 4, 5]
print(all(l))
# True
# all values false
l = [0, False]
print(all(l))
# False
```

#### any()

The any() function returns True if any element of an iterable is True. If not, any() returns False.

```python
# True since 1,3 and 4 (at least one) is true
l = [1, 3, 4, 0]
print(any(l))
# True
# False since both are False
l = [0, False]
print(any(l))
# False
```

#### abs()

The abs() method returns the absolute value of the given number. If the number is a complex number, abs() returns its magnitude.

```python
# random integer
integer = -20
print('Absolute value of -20 is:', abs(integer))
# 20
# random complex number
complex = (3 - 4j)
print('Magnitude of 3 - 4j is:', abs(complex))
# Magnitude of 3 - 4j is: 5.0
```