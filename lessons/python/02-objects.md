---
layout: page
title: Programming with Python
subtitle: Data types
minutes: 30
---
> ## Learning Objectives {.objectives}
>
> *   Identify built-in data types in Python
> *   Differentiate between scalar and structured objects
> *   Recognize mutable and immutable objects
> *   Convert between data types in Python

Before we go much further into numerical modeling, we should stop and discuss some of the inner workings of Python. Recognizing the way values can be handled by Python will give you flexibility in programming and help you avoid common errors.

Early in the previous lesson, we saw that we could assign a value to a variable using the symbol `=`:


~~~ {.python}
elevation_ft = 5430    # elevation of Boulder, CO in feet 
~~~
<BR>

>## Documentation is important!  {.callout}
>
>One way to include documentation in your programs is with comments. Comments are text within the code that the computer ignores. In Python, comments start with the symbol `#`.

The variable name `elevation_ft` is not itself the value 5430. It is simply a label that points to a place in the memory where the **object** with the value `5430` is stored.

This is different from the way the symbol = is used in algebra. An equation like this one represents different things in Python and in algebra:


~~~ {.python}
x = 4 + 1
~~~

In both cases, the letter 'x' corresponds to the value 5. In algebra, 'x' is equivalent to 5; the symbol is simply taking the place of the number. In Python, 'x' is not itself 5; it is a name that points to an object with a value of 5. The variable name 'x' is short-hand for the address where the object is stored in the memory.
<BR>

>## What is an object?  {.callout}
>
>We can think of objects as the things that Python programs manipulate.
>
>Different programming languages define "object" in different ways. *Everything in Python is an object* and almost everything has attributes and methods. Strings are objects. Lists are objects. Functions are objects. Even modules are objects.

Objects are classified into different **classes** or **data types** that define the kinds of things that a program can do with those objects. An integer (like `5430` above) is one type of object, the string "Hello, World!" is also an object, and the numpy array of elevation values in the previous lesson was another type of object.

## Scalar objects

Objects are either **scalar** or **non-scalar**. Scalar objects are the building blocks of data. They hold a single value and cannot be divided. *Non-scalar* objects hold sets of elements within some internal structure. Computers operate directly on scalar objects but have to iterate through the elements of a non-scalar object in order to process it.

The term *scalar* comes from linear algebra, where it is used to differentiate a single number from a vector or matrix. 

### - Integers

We can use the built-in function `type` to see what type a particular object is:

~~~ {.python}
type(5430)
~~~
~~~ {.output}
int
~~~


The number `5430` is an object of type **int**, or integer. We can also use `type` see the type of  object that the variable is assigned to:


~~~ {.python}
type(elevation_ft)
~~~
~~~ {.output}
int
~~~


The variable name `elevation_ft` is assigned to an object with the value `5430`, which is of type int. Integer is one of several built-in data types in Python. Because they are built in, we don’t need to load a library to use them.

### - Floats

Real numbers (*potentially* with decimals) are floating point numbers or **floats**:

~~~ {.python}
elevation_m = 1655.064 # elevation of Boulder, CO in meters

type(elevation_m)
~~~
~~~ {.output}
float
~~~

A number doesn't need to have meaningful fractional part to be a float. Just adding a decimal point to a whole number makes it a float:

~~~ {.python}
print '7 is', type(7)
print '-' * 20
print '7. is', type(7.)
print '7.0 is', type(7.0)
~~~
~~~ {.output}
7 is <type 'int'>
--------------------
7. is <type 'float'>
7.0 is <type 'float'>
~~~

>## Math with integers and floats  {.callout}
>
>One would expect that a programming language would follow the same rules of arithmatic that we learned as kids. Confusingly, that’s not always the case:
>
>
>~~~ {.python}
>print '7/2 =', 7/2
>~~~
>~~~ {.output}
>7/2 = 3
>~~~
>
>In the real world, half of 7 is 3.5! Why is it behaving this way?
>
>In Python 2 (but not Python 3!), dividing an integer (the number 7) by another integer (the number 2) always results in an integer. This is known as **integer division**. If either number is a float, though, division behaves as expected and returns a float:
>
>
>~~~ {.python}
>print '7.0000000001/2 =', 7.0000000001/2
>~~~
>~~~ {.output}
>7.0000000001/2 = 3.50000000005
>~~~
>
>While this might seem strange and unnecessarily annoying, some programming languages use integer division for historical reasons: integers take up less memory space and integer operations were much faster on early machines.
>
>Read more about it on [Guido van Rossum's blog on the history of Python](http://python-history.blogspot.com/2010/08/why-pythons-integer-division-floors.html) (Guido is the inventor of Python!).
>

>## Converting between types {.callout}
>
>Division is not the only operation where we have to worry about the data type of the objects we are using. Many other Python functions are also sensitive to the type of object they receive.
>
>You will often find yourself needing to convert variables from one data type to another. This is called **casting**. Luckily, conversion functions are easy to remember: the type names double up as a conversion function!
>
>To convert an integer to a float, use the function **float()**:
>
>~~~ {.python}
>num_int = 7
>
>print 'integer division:', num_int / 2
>print 'after casting:', float(num_int) / 2
>~~~
>~~~ {.output}
>integer division: 3
>after casting: 3.5
>~~~
>
>To convert a float into an integer, use the function **int()**:
>
>~~~ {.python}
>num_float = 7.0
>
>print "'normal' division:", num_float / 2
>print 'after casting:', int(num_float) / 2
>~~~
>~~~ {.output}
>'normal' division: 3.5
>after casting: 3
>~~~

### - Booleans

Other types of objects in Python are a bit more unusual. **Boolean** objects can take one of two values: True or Falls. We will see in a later lesson that boolean objects are produced by operations that compare values against one another and by conditional statements.

You'll notice that the words True and False change color when you type them into a Jupyter Notebook. They look different because they are recognized as special keywords. This only works when True and False are capitalized, though! Python does not treat lower case true and false as boolean objects.


~~~ {.python}
i_like_chocolate = True
type(i_like_chocolate)
~~~
~~~ {.output}
bool
~~~
<BR>

When used in an arithmetic operation, a boolean object acts like an integer. True takes a value of 1 and False a value of 0:

~~~ {.python}
print '3 * True:', 3 * True
print '3.0 * True:', 3.0 * True
print '3.0 * False:', 3.0 * False
~~~
~~~ {.output}
3 * True: 3
3.0 * True: 3.0
3.0 * False: 0.0
~~~
<BR>

We can cast objects of any type into a boolean using the function **bool()**:

~~~ {.python}
print bool(127.3)
~~~
~~~ {.output}
True
~~~

### - NoneType

The most abstract of data types in Python is the **NoneType**. NoneType objects can only contain the special constant **None**. `None` is the value that an object takes when no value is set or in the absence of a value. `None` is a null or NoData value. It is not the same as False, it is not 0 and it is not an empty string. `None` is nothing.

If you compare `None` to anything other than `None`, `None` will always be less than the other value (In Python 3, comparing `None` to another object will instead produce an error):


~~~ {.python}
nothing = None
print type(nothing)

print nothing > -4
print nothing == nothing   # double == compares for equivalency
~~~
~~~ {.output}
<type 'NoneType'>
False
True
~~~

Why would you ever want to create an object that contains nothing at all? As you build more complex programs, you'll find many situations where you might want to set a variable but don't want to assign a value to it quite yet. For example, you might want your code to perform one action if the user sets a certain variable but perform a different action if the user does nothing:


~~~ {.python}
input_from_user = None

# The user might or might not provide input here.
# If the user provides input, the value would be
# assigned to the variable input_from_user

if input_from_user is None:
    print "The user hasn't said anything!"
    
if input_from_user is not None:
    print "The user said:", input_from_user
~~~
~~~ {.output}
The user hasn't said anything!
~~~
<BR>

Try assigning an object of a different type to `input_from_user` to see how the script behaves.

>## Who's who in memory {.callout}
>You can use the `whos` command to see what variables you have created and what modules you have loaded into the memory. This is an iPython command, so it will only work if you are in an iPython terminal or a Jupyter Notebook.
>
>
>~~~ {.python}
>whos
>~~~
>~~~ {.output}
>Variable           Type        Data/Info
>----------------------------------------
>elevation_ft       int         5430
>elevation_m        float       1655.064
>i_like_chocolate   bool        True
>input_from_user    NoneType    None
>nothing            NoneType    None
>x                  int         5
>~~~

>## Numeric data types  {.challenge}
>What type of object are these values?
>
>- 5.6
>- 1932
>- 22.
>- 7.0000
>
>>## Solution{.solution}
>>
>>- float
>>- int
>>- float
>>- float

>## Casting and integer division  {.challenge}
>
>Think about the operations that occur when running the following statements. Why are their outputs different?
>
>~~~ {.python}
>print 'a:', 100/3
>print 'b:', float(100)/3
>print 'c:', 100/float(3)
>print 'd:', float(100/3)
>~~~
>
>>## Solution{.solution}
>>
>>~~~ {.output}
>>a: 33
>>b: 33.3333333333
>>c: 33.3333333333
>>d: 33.0
>>~~~
>>
>> (a) Dividing two integers results in an integer
>> (b),(c) Casting either the dividend or divisor as a float will mean that it is no longer integer division
>> (d) The function `float()` is acting on the output of integer division. The remainder has already been discarded.

>## Lemonade sales {.challenge}
>
>You get hired to work for a highly successful lemonade stand. Their database is managed by a 7-year-old, though, so their data is a mess. These are their sales reports for FY2017:
>
>
>~~~ {.python}
>sales_1q = ["50.3"] # thousand dollars
>sales_2q = 108.52
>sales_3q = 79
>sales_4q = "82"
>~~~
>~~~ {.output}
>
>- Calculate the total sales for FY2017
>~~~
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>total_sales = float(sales_1q[0]) + sales_2q + sales_3q + float(sales_4q)
>>print 'Total lemonade sales:', total_sales, 'thousand dollars'
>>~~~
>>~~~ {.output}
>>Total lemonade sales: 319.82 thousand dollars
>>~~~

>## Casting bool  {.challenge}
>
>Any type of object can be cast to a boolean with the function *bool()*. Which of these objects converts to True and which to False?
>
>- a negative float
>- None
>- the boolean object True
>- the integer 0
>- the float 0
>- the string 'string'
>- an empty string
>- a string that contains only a space
>- 3e-324
>- 2e-324
>- a list with one item
>- an empty list
>
>>## Solution{.solution}
>>
>>- a negative float: True
>>- None: False
>>- the boolean object True: True
>>- the integer 0: False
>>- the float 0.0: False
>>- the string 'string': True
>>- an empty string: False
>>- a string that contains only a space: True
>>- 3e-324: True
>>- 2e-324: False
>>- a list with one item: True
>>- an empty list: False



## Non-scalar (or structured) objects

*Non-scalar* objects contain multiple elements that can be separated into parts. Since they have an internal structure, we can use **indexing** to access the individual parts of a non-scalar object.

There are several built-in types of non-scalar objects in Python. They can be grouped according to their internal structure:

- **Sequences** are structured objects where elements are kept in a known order. We use **integer indexing** and **slicing** to access elements based on their position.

- **Mapping** objects map keys to values. Because the elements of a mapping object are not stored in order, we cannot select them based on their position. Instead, the keys serve as indices.

The differences between the two groups will make more sense after looking at some examples.
<BR>

### Sequences

### - Strings

Objects of type **string** are simply sequences of characters with a defined order. Strings have to be enclosed in sigle quotes (' '), double quotes (" "), triple single or double quotes (''' ''', """ """), or single quotes within double quotes ("' '"):


~~~ {.python}
print type("The judge said 'Nobody expects the Spanish Inquisition!'")
~~~
~~~ {.output}
<type 'str'>
~~~

We can cast objects of any type into strings with the function **str()**:

~~~ {.python}
str(bool(6 < 2))
~~~
~~~ {.output}
'False'
~~~

We can test if a sub string exists within a string or not using the keyword **in**:

~~~ {.python}
print 'a' in 'program'
print 'at' not in 'battle'
~~~
~~~ {.output}
True
False
~~~

There are many methods available for objects of type string:

~~~ {.python}
string = "if it's in caps i'm trying to YELL!"

print string.lower()
print string.upper()
print string.capitalize()
print string.split()
print string.replace('YELL', 'fix my keyboard')
~~~
~~~ {.output}
if it's in caps i'm trying to yell!
IF IT'S IN CAPS I'M TRYING TO YELL!
If it's in caps i'm trying to yell!
['if', "it's", 'in', 'caps', "i'm", 'trying', 'to', 'YELL!']
if it's in caps i'm trying to fix my keyboard!
~~~

### - Lists

A **list** is exactly what it sounds like – a sequence of things. The objects contained in a list don’t have to be of the same type: one list can simultaneously contain numbers, strings, other lists, numpy arrays, and even commands to run. Like other sequences, lists are ordered. We can access the individual items in a list through an integer index.

Lists are created by putting values, separated by commas, inside square brackets:

~~~ {.python}
shopping_list = ['funions', 'ice cream', 'guacamole']
~~~

We can change the individual values in a list using indexing:

~~~ {.python}
shopping_list[0] = 'funyuns' # oops
print shopping_list
~~~
~~~ {.output}
['funyuns', 'ice cream', 'guacamole']
~~~
<BR>

There are many ways to change the contents of lists besides assigning new values to individual elements:

~~~ {.python}
shopping_list.append('tortilla chips')   # add one item
print shopping_list
~~~
~~~ {.output}
['funyuns', 'ice cream', 'guacamole', 'tortilla chips']
~~~
<BR>

~~~ {.python}
del shopping_list[0]   # delete the first item
print shopping_list
~~~
~~~ {.output}
['ice cream', 'guacamole', 'tortilla chips']
~~~
<BR>

~~~ {.python}
shopping_list.reverse()   # reverse the order of the list (in place)
print shopping_list
~~~
~~~ {.output}
['tortilla chips', 'guacamole', 'ice cream']
~~~
<BR>

>## Overloading  {.callout}
>
>`+` usually means addition, but when used on strings or lists, it means “concatenate”. The multiplication operator `*` used on a list replicates elements of the list and concatenates them together:
>
>~~~ {.python}
>counts = [2, 4, 6, 8, 10]
>repeats = counts * 2
>print repeats
>~~~
>
>~~~ {.output}
>[2, 4, 6, 8, 10, 2, 4, 6, 8, 10]
>~~~
>
>This is equivalent to:
>
>~~~ {.python}
>counts + counts
>~~~
>
>The technical term for this is operator overloading: a single operator, like `+` or `*`, can do different things depending on what type of object it’s applied to.
<BR>

We can use operators to concatenate lists or build lists with repeated elements:

~~~ {.python}
shopping_list = shopping_list + ['coffee', 'cheese']
print shopping_list
~~~
~~~ {.output}
['tortilla chips', 'guacamole', 'ice cream', 'coffee', 'cheese']
~~~
<BR>

~~~ {.python}
print 3 * shopping_list[-1:]
~~~
~~~ {.output}
['cheese', 'cheese', 'cheese']
~~~
<BR>

There is one very important difference between lists and strings: **lists can be modified in place while strings cannot**.
<BR>
<BR>

>## Ch-ch-changes  {.callout}
>
>Data which can be modified in place is called **mutable**, while data which cannot be modified is called **immutable**. Strings, numbers and tuples are immutable. This does not mean that variable names assigned to these objects will forever be assigned to those objects! While we can use indexing to access individual values in an immutable object, we can't use indexing to modify them:
>
>~~~ {.python}
>fav_animal = 'capibara' # misspelled!
>print fav_animal[3]
>
>fav_animal[3] = 'y' # change to capybara
>~~~
>~~~ {.output}
>i
>---------------------------------------------------------------------------
>TypeError                                 Traceback (most recent call last)
><ipython-input-133-936dce908564> in <module>()
>      2 print fav_animal[3]
>      3 
>----> 4 fav_animal[3] = 'y' # change to capybara
>
>TypeError: 'str' object does not support item assignment
>~~~
>If we want to change the value of a string, number, or tuple, we do it by re-assigning the variable name to a completely new object:
>
>~~~ {.python}
>fav_animal2 = fav_animal # both variable names point to same object
>
>fav_animal2 = 'capybara' # re-assign variable name to new object
>
>print 'Old object:', fav_animal
>print 'New object:', fav_animal2
>~~~
>~~~ {.output}
>Old object: capibara
>New object: capybara
>~~~
>
>Lists and numpy arrays are *mutable* objects: we can modify them in place after they have been written to memory. We can change individual elements, append new elements, or reorder the whole list. For operations like sorting, we can choose whether to use a function that modifies the data in place or a function that leaves the original object unchanged and creates a new, modified object with a new variable name.
><BR><BR>
>
>Be careful when modifying data in place. **If two variables refer to the same list and you modify a value in the list, it will change the contents of the list for both variables.** If you want to have two variables refer to independent versions of the same mutable object, you must make a copy of the object when you assign it to the new variable name.
><BR><BR>
>
>Consider the relationship between variable names and objects in this script:
>
>~~~ {.python}
>mildSalsa = ['peppers', 'onions', 'cilantro', 'tomatoes']
>
>hotSalsa = mildSalsa           # both salsas point to the same object
>hotSalsa[0] = 'jalapenos'      # change the recipe for hot salsa
>
>print 'Mild salsa:', mildSalsa
>print 'Hot salsa:', hotSalsa
>~~~
>~~~ {.output}
>Mild salsa: ['jalapenos', 'onions', 'cilantro', 'tomatoes']
>Hot salsa: ['jalapenos', 'onions', 'cilantro', 'tomatoes']
>~~~
>
>Because both variable names `mildSalsa` and `hotSalsa` point to the same mutable object, changing the recipe for one also changed the recipe for the other.
><BR>
><BR>
>
>If we want variables with mutable values to be independent, we must make a copy of the object:
>
>
>~~~ {.python}
>mildSalsa = ['peppers', 'onions', 'cilantro', 'tomatoes']
>
>hotSalsa = list(mildSalsa)      # make a copy of the list
>hotSalsa[0] = 'jalapenos'       # change the recipe for hot salsa
>
>print 'Mild salsa:', mildSalsa
>print 'Hot salsa:', hotSalsa
>~~~
>~~~ {.output}
>Mild salsa: ['peppers', 'onions', 'cilantro', 'tomatoes']
>Hot salsa: ['jalapenos', 'onions', 'cilantro', 'tomatoes']
>~~~
>
>Code that modifies data in place can be more difficult to understand (and therefore to debug). However, it is often far more efficient to modify a large data structure in place than to create a modified copy for every small change. You should consider both of these aspects when writing your code.

>## Object addresses  {.callout}
>
>We can find the address of an object in memory with the function `id()`. This function returns the “identity” of an object: an integer which is guaranteed to be unique and constant for this object during its lifetime.
>
>Two variables names that point to the same mutable object will show the same ID.
>
>
>~~~ {.python}
>mildSalsa = ['peppers', 'onions', 'cilantro', 'tomatoes']
>hotSalsa = mildSalsa
>
>print 'Variable 1 to mutable obj:', id(mildSalsa)
>print 'Variable 2 to mutable obj:', id(hotSalsa)
>~~~
>~~~ {.output}
>Variable 1 to mutable obj: 4548266248
>Variable 2 to mutable obj: 4548266248
>~~~
>
>When the second variable name is tied to an independing copy of the mutable object, the two variable names will have different IDs:
>
>
>~~~ {.python}
>hotSalsa = list(mildSalsa) # copies the object
>
>print 'Original mutable obj:', id(mildSalsa)
>print 'Copied mutable obj:', id(hotSalsa)
>~~~
>~~~ {.output}
>Original mutable obj: 4548266248
>Copied mutable obj: 4551753672
>~~~

> ## Nested Lists {.callout}
>
> Since lists can contain any Python variable, it can even contain other lists.
>
> For example, we could represent the products in the shelves of a small grocery shop:
>
> ~~~{.python}
> x = [['pepper', 'zucchini', 'onion'],
>      ['cabbage', 'lettuce', 'garlic'],
>      ['apple', 'pear', 'banana']]
> ~~~
>
> Here is a visual example of how indexing a list of lists `x` works:
>
> <a href='https://twitter.com/hadleywickham/status/643381054758363136'>
> ![The first element of a list. Adapted from @hadleywickham's tweet about R lists.](figs/indexing_lists_python.png)</a>
>
> Using the previously declared list `x`, these would be the results of the
> index operations shown in the image:
>
> ~~~{.python}
> print [x[0]]
> print x[0]
> print x[0][0]
> ~~~
> ~~~{.output}
> [['pepper', 'zucchini', 'onion']]
> ['pepper', 'zucchini', 'onion']
> 'pepper'
> ~~~
>
> Thanks to [Hadley Wickham](https://twitter.com/hadleywickham/status/643381054758363136)
> for the image above.


### - Tuples

Like lists, **tuples** are simply sequences of objects. Tuples, however, are *immutable* objects. We can only change the values in a tuple by assigning the variable name to a new object.

Tuples are created by putting values in a sequence, separated by commas. For easier reading, they are usually inside parentheses:

~~~ {.python}
things = ('toy cars', 42, 'dinosaur')
print type(things)
~~~
~~~ {.output}
<type 'tuple'>
~~~

Because they are sequences, we can use indexing to access individual values in a tuple:

~~~ {.python}
print things[0]
~~~
~~~ {.output}
toy cars
~~~

However, because they are *immutable* objects, we cannot use indexing to change the values of a tuple:

~~~ {.python}
things[0] = 'toy airplanes'
~~~
~~~ {.output}
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-151-546e5c83c872> in <module>()
----> 1 things[0] = 'toy airplanes'

TypeError: 'tuple' object does not support item assignment
~~~


### Mapping types

### - Dictionaries

Because values in sequences are stored a known order, individual values in sequence-type objects can be accessed by their position through integer indices. **Dictionaries** are a type of object where values are not stored in any particular order. Dictionaries are unordered collections of **key:value** pairs. They map (or match) keys, which can be any immutable type (strings, numbers, tuples), to values, which can be of any type (heterogeneous). Individual values in a dictionary are accessed by their keys.

We create dictionaries with curly brackets and pairs of keys and values. An empty dictionary would simply have no key:value pairs inside the curly brackets:

~~~ {.python}
person = {'name':'Jack', 'age': 32}
print person
~~~
~~~ {.output}
{'age': 32, 'name': 'Jack'}
~~~

Notice that the order of the key:value pairs is different in the dictionary definition than in the output! Because values in a dictionary are not stored in a particular order, they take an arbitrary order when the dictionary is displayed.
<BR>

We can access and modify individual values in a dictionary with their keys:

~~~ {.python}
person['age'] = 33
print person
~~~
~~~ {.output}
{'age': 33, 'name': 'Jack'}
~~~

We can also use keys to add values to a previously defined dictionary:

~~~ {.python}
person['address'] = 'Downtown Boulder'  
print person
~~~
~~~ {.output}
{'age': 33, 'name': 'Jack', 'address': 'Downtown Boulder'}
~~~
<BR>

>## String methods {.challenge}
>
> Can you explain what this script does?
>
>~~~ {.python}
>string = "if it's in caps i'm trying to YELL!"
>
>print string.find('caps')
>~~~
>
>- Modify the command so that it finds the substring ('caps') even if capitalization is different in the string (ex. 'CAPS').
>
>- What is the output of `find` if the substring is not in the string?
>
>- What happens if the substring appears more than once in the string? (ex. 'in')
>
>>## Solution{.solution}
>>
>>~~~{.python}
>>loc = string.find('caps')
>>print string[loc:]
>>~~~
>>~~~ {.output}
>>caps i'm trying to YELL!
>>~~~
>>
>>The method `find` returns the start index of the substring.
>>
>>~~~{.python}
>># change capitalization for testing
>>string = "if it's in cAPs i'm trying to YELL!"
>>
>>print 'If substring not in string:', string.find('caps')
>>
>># force string to lowercase
>>print 'If find substring:', string.lower().find('caps')
>>
>>print "Returns only first occurrence of substring 'in':", string.lower().find('in')
>>~~~
>>~~~ {.output}
>>If substring not in string: -1
>>If find substring: 11
>>Returns only first occurrence of substring 'in': 8
>>~~~

>## Numbers in strings {.challenge}
>
>You decided to quit research and open a bar. You are using Python to create a sign.
>
>~~~ {.python}
>age = 21   # <--- don't change this line!
>sign = 'You must be ' + age + '-years-old to enter this bar'
>print sign
>~~~
>~~~ {.output}
>---------------------------------------------------------------------------
>
>TypeError                                 Traceback (most recent call last)
>
><ipython-input-28-253b33d26e7e> in <module>()
>      1 age = 21   # <--- don't change this line!
>----> 2 sign = 'You must be ' + age + '-years-old to enter this bar'
>      3 print sign
>
>
>TypeError: cannot concatenate 'str' and 'int' objects
>~~~ 
>
>Fix your code so it prints the text in `sign` correctly. Don't change the first line!
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>age = 21
>>sign = 'You must be ' + str(age) + '-years-old to enter this bar'
>>print sign
>>~~~
>>~~~ {.output}
>>You must be 21-years-old to enter this bar
>>~~~


>## Cheeeeeeeeese  {.challenge}
>
>What is the difference between these two statements? Why are their outputs different?
>
>~~~ {.python}
>s1 = 3 * shopping_list[-1:]
>s2 = 3 * shopping_list[-1]
>~~~
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>print s1, type(s1)
>>print s2, type(s2)
>>~~~
>>~~~ {.output}
>>['cheese', 'cheese', 'cheese'] <type 'list'>
>>cheesecheesecheese <type 'str'>
>>~~~
>>
>>`shopping_list[-1]` is the last value in the list, which is a string. The second statement is therefore repeating a string three times.
>>
>>`shopping_list[-1:]` is a slice of a list, so it is also a list (even if it only has one value). The first statement is therefore repeating a list three times.

>## Human readable numbers  {.challenge}
>
>When we write down a large integer, it's customary to use commas (or periods, depending on the country) to separate the number into groups of three digits. It's easier for humans to read a large number with separators but Python sees them as something else. What type of object is this? Why does Python read it as this object type?
>
>~~~ {.python}
>my_account_balance = 15,752,000,000
>~~~
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>my_account_balance = 15,752,000,000
>>type(my_account_balance)
>>~~~
>>~~~ {.output}
>>tuple
>>~~~
>>
>> You don't actually need the parentheses to create a tuple. Python reads any sequence of objects separated by commas as a tuple.


>## Tiny tuples  {.challenge}
>
>Create a tuple that contains only one value. Confirm that it's really a tuple. You might have to experiment!
>
>Hint: Start with a tuple with two values and simplify it.
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>lil_tuple = 1,
>>type(lil_tuple)
>>~~~
>>~~~ {.output}
>>tuple
>>~~~

>## Travel guide  {.challenge}
>
>- Create an empty dictionary called "states"
>- Add 3 items to the dictionary. Map state names (the keys) to their abbreviations (the values) (ex. 'Wyoming':'WY'). Pick easy ones!
>You can also use states from another country or look [here](http://www.50states.com/abbreviations.htm) for help.
>
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>states = {}
>>
>>states['Colorado'] = 'CO'
>>states['California'] = 'CA'
>>states['Florida'] = 'FL'
>>~~~
>
>- Use a variable in place of a key to access values in your `states` dictionary. For example, if I set the variable to "Wyoming", the value should be "WY".
>
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>selected_state = 'California'
>>
>>print states[selected_state]
>>~~~
>>~~~ {.output}
>>CA
>>~~~
>
>
>- Create a dictionary called "cities" that contains 3 key:value pairs. The keys should be the state abbreviation in your `states` dictionary and the values should be the names of one city in each of those states state (ex. 'WY':'Laramie'). Don't start with an empty dictionary and add values to it -- initialize the dictionary with the all of the key:value pairs already in it.
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>cities = {'CO':'Denver', 'FL':'Miami', 'CA':'San Francisco'}
>>~~~

>## Travel guide, part II (Advanced)  {.challenge}
>
>- Write a short script to fill in the blanks in this string for any state in your `states` dictionary.
>
>       \_\_\_\_\_\_\_\_\_\_ is abbreviated \_\_\_\_ and has cities like \_\_\_\_\_\_\_\_
>
>- Refactor (rewrite, improve) your code so you only have to change one word in your script to change states.
>
>Hint: The values in one of your dictionaries are the keys for the other dictionary
>
>>## Solution{.solution}
>>
>>
>>~~~ {.python}
>>selected_state = 'Colorado'
>>
>>print selected_state + ' is abbreviated ' + states[selected_state] + ' and has cities like ' + cities[states[selected_state]]
>>~~~
>>~~~ {.output}
>>Colorado is abbreviated CO and has cities like Denver
>>~~~


