## Day 14 Task: Python Data Types and Data Structures for DevOps

### New day, New Topic.... Let's learn along 😉

### Data Types
- Data types are the classification or categorization of data items. It represents the kind of value that tells what operations can be performed on a particular data. 
- Since everything is an object in Python programming, data types are actually classes and variables are instance (object) of these classes.
- Python has the following data types built-in by default: Numeric(Integer, complex, float), Sequential(string,lists, tuples), Boolean, Set, Dictionaries, etc

To check what is the data type of the variable used, we can simply write:
```your_variable=100```
```type(your_variable)```

### Data Structures

 Data Structures are a way of organizing data so that it can be accessed more efficiently depending upon the situation. Data Structures are fundamentals of any programming language around which a program is built. Python helps to learn the fundamental of these data structures in a simpler way as compared to other programming languages.

- Lists
Python Lists are just like the arrays, declared in other languages which is an ordered collection of data. It is very flexible as the items in a list do not need to be of the same type

- Tuple
Python Tuple is a collection of Python objects much like a list but Tuples are immutable in nature i.e. the elements in the tuple cannot be added or removed once created. Just like a List, a Tuple can also contain elements of various types.

- Dictionary
Python dictionary is like hash tables in any other language with the time complexity of O(1). It is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds the key:value pair. Key-value is provided in the dictionary to make it more optimized



















## Tasks
1. Give the Difference between List, Tuple and set. Do Handson and put screenshots as per your understanding.




   <pre>
#### List:

Ordered collection of items.

Mutable, meaning you can change, add, or remove elements after the list is defined.

Created using square brackets [].

Allows duplicate elements.

Example:

python

<code>my_list = [1, 2, 3, 'a', 'b', 'c']</code>







#### Tuple:

Ordered collection of items.

Immutable, meaning you cannot change, add, or remove elements after the tuple is defined.

Created using parentheses ().

Allows duplicate elements.

Example:

python

<code>my_tuple = (1, 2, 3, 'a', 'b', 'c')</code>








#### Set:

Unordered collection of unique items.
Mutable, meaning you can add or remove elements, but you cannot change individual elements.
Created using curly braces {} or the set() constructor.
Does not allow duplicate elements.
Example:
python
Copy code
my_set = {1, 2, 3, 'a', 'b', 'c'}
Now, for a hands-on understanding, you can try creating and manipulating these data structures in a Python environment like an IDE or Jupyter Notebook. Here's a simple example using Python in a Jupyter Notebook:






# List example
<code>
my_list = [1, 2, 3, 'a', 'b', 'c']
print("List:", my_list)

# Tuple example
my_tuple = (1, 2, 3, 'a', 'b', 'c')
print("Tuple:", my_tuple)

# Set example
my_set = {1, 2, 3, 'a', 'b', 'c'}
print("Set:", my_set)
</code>





Feel free to experiment with adding, removing, or modifying elements in each data structure to observe their behavior.
   </pre>


   
2. Create below Dictionary and use Dictionary methods to print your favourite tool just by using the keys of the Dictionary.
```
fav_tools = 
{ 
  1:"Linux", 
  2:"Git", 
  3:"Docker", 
  4:"Kubernetes", 
  5:"Terraform", 
  6:"Ansible", 
  7:"Chef"
}
```
![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/6c85575b-27a5-4d3c-b13a-f89ef54795ca)



3. Create a List of cloud service providers
eg.
```
cloud_providers = ["AWS","GCP","Azure"]
```
![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/cbe789f2-d4b5-4886-8156-ac375014d4a8)

Write a program to add `Digital Ocean` to the list of cloud_providers and sort the list in alphabetical order.

![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/9eb6ad0e-14bd-4f54-a850-1e89a4ee674b)


[Hint: Use keys to built in functions for Lists]

If you want to deep dive further, Watch [Python](https://youtu.be/abPgj_3hzVY)

You can share the learning with everyone over linkedin and tag us along 😃
