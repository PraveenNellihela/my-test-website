---
type: PostLayout
title: A Comprehensive Guide to Python Lists
colors: colors-b
date: '2022-08-20'
author: content/data/team/doris-soto.json
excerpt: >-
  Everything a coder need to know about Python lists, from beginner to advanced
  levels.
featuredImage:
  type: ImageBlock
  url: /images/howard-bouchevereau-Ql4Y26OsEoY-unsplash.jpg
  altText: >-
    Foto de <a
    href="https://unsplash.com/es/@howardbouchevereau?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Howard
    Bouchevereau</a> en <a
    href="https://unsplash.com/es/fotos/black-flat-screen-computer-monitor-on-brown-wooden-desk-Ql4Y26OsEoY?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
  caption: >-
    Foto de <a
    href="https://unsplash.com/es/@howardbouchevereau?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Howard
    Bouchevereau</a> en <a
    href="https://unsplash.com/es/fotos/black-flat-screen-computer-monitor-on-brown-wooden-desk-Ql4Y26OsEoY?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
backgroundImage:
  type: BackgroundImage
  url: /images/bg4.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 2
bottomSections:
  - elementId: ''
    type: RecentPostsSection
    colors: colors-f
    variant: variant-d
    subtitle: Recent posts
    showDate: true
    showAuthor: false
    showExcerpt: true
    recentCount: 2
    styles:
      self:
        height: auto
        width: wide
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-12
          - pb-56
          - pr-4
          - pl-4
        justifyContent: center
      title:
        textAlign: left
      subtitle:
        textAlign: left
      actions:
        justifyContent: center
    showFeaturedImage: true
    showReadMoreLink: true
  - type: ContactSection
    backgroundSize: full
    title: Stay up-to-date with my words ✍️
    colors: colors-f
    form:
      type: FormBlock
      elementId: sign-up-form
      fields:
        - name: firstName
          label: First Name
          hideLabel: true
          placeholder: First Name
          isRequired: true
          width: 1/2
          type: TextFormControl
        - name: lastName
          label: Last Name
          hideLabel: true
          placeholder: Last Name
          isRequired: false
          width: 1/2
          type: TextFormControl
        - name: email
          label: Email
          hideLabel: true
          placeholder: Email
          isRequired: true
          width: full
          type: EmailFormControl
        - name: updatesConsent
          label: Sign me up to recieve my words
          isRequired: false
          width: full
          type: CheckboxFormControl
      submitLabel: "Submit \U0001F680"
      styles:
        submitLabel:
          textAlign: center
    styles:
      self:
        height: auto
        width: wide
        margin:
          - mt-0
          - mb-0
          - ml-4
          - mr-4
        padding:
          - pt-24
          - pb-24
          - pr-4
          - pl-4
        alignItems: center
        justifyContent: center
        flexDirection: row
      title:
        textAlign: left
      text:
        textAlign: left
media:
  type: ImageBlock
  url: /images/howard-bouchevereau-Ql4Y26OsEoY-unsplash.jpg
  altText: >-
    Foto de <a
    href="https://unsplash.com/es/@howardbouchevereau?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Howard
    Bouchevereau</a> en <a
    href="https://unsplash.com/es/fotos/black-flat-screen-computer-monitor-on-brown-wooden-desk-Ql4Y26OsEoY?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
  caption: >-
    Foto de <a
    href="https://unsplash.com/es/@howardbouchevereau?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Howard
    Bouchevereau</a> en <a
    href="https://unsplash.com/es/fotos/black-flat-screen-computer-monitor-on-brown-wooden-desk-Ql4Y26OsEoY?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>      
  elementId: ''
---
Lists are a one of the four built in data structures found in Python. Data structures can be considered as “containers” that help organize, manage and store data in a unique way. 

In addition to the built in data structures, Python also offers developers the ability to create their own. These are known as user-defined data structures. Today, we will look at the built in data structure, lists. We will dive deeper into the other data structures in future guides in this series.

## Table of Contents

*   List creation and indexing

*   The methods of list objects

*   List Slicing

*   List Comprehension

*   Other useful tips

<p align="center">
![](/images/python1.webp)
<em>Data structures found in Python.</em>
</p>

## List creation and indexing

### How to create a list

There are different ways to create a list in Python. You can add elements by putting them in-between square brackets and separated by a comma. The elements can be of different types, such as strings, integers, floats and even data structures such as lists.

```
# create a list by adding elements within square brackets: 
list_a = ["banana", 42, [], 24.08, True]  

# create a new empty list with the list function (items can be appended later):
list_b = list()

# different data types such as integers, bolean, strings, lists etc.
# are allowed. duplicates are also allowed, as shown below. 
list_types = ["apple", True, list_a, 42, True] 
```

## How to access elements inside a list

Items inside a list can be accessed by **indexing**. Indexing allows a user to access items within an *iterable* (objects that can be looped over, such as lists), based on the items position. Keep in mind however, that the very first position is defined by 0 and not 1. Indexing can be done in reverse too, by specifying a negative index. For example, the last element can be accessed by providing -1 as the index. Let us look at indexing in practice:

```
my_list = ["Pepé Le Pew", "Marvin the Martian", "bugs", "sylvester", "daffy", "Wile E. Coyote"]

skunk = my_list[0]  # first element is accessed with the index 0
rabbit = my_list[2]

# if an element does not exist for given index, an IndexError will be raised. 
acme = my_list[101] 

# indexing can be done in reverese too. 
super_genius = my_list[-1]
duck = my_list[-2] 

print(duck)
```

## How to access elements inside a list

Items inside a list can be accessed by **indexing**. Indexing allows a user to access items within an *iterable* (objects that can be looped over, such as lists), based on the items position. Keep in mind however, that the very first position is defined by 0 and not 1. Indexing can be done in reverse too, by specifying a negative index. For example, the last element can be accessed by providing -1 as the index. Let us look at indexing in practice:

```

my_list = ["Pepé Le Pew", "Marvin the Martian", "bugs", "sylvester", "daffy", "Wile E. Coyote"]

skunk = my_list[0]  # first element is accessed with the index 0
rabbit = my_list[2]

# if an element does not exist for given index, an IndexError will be raised. 
acme = my_list[101] 

# indexing can be done in reverese too. 
super_genius = my_list[-1]
duck = my_list[-2] 

print(duck)
```

As mentioned above, a list is an *iterable*. This means we can loop over a list with a for loop to access items and carry out various operations. For example, you can loop over an print all the elements inside the list. Another more useful thing you can do is loop over to see if an item you want is inside a given list. You can also use this method to create new lists using **list comprehension**, which we will discuss later in this guide. Here is a more simple example in practice:

```
new_list = ["Cappuccino", "Espresso", "Latte", "Americano", "Mocha"]

# print all items in the list: 
for coffee in new_list:
  print(coffee)

# check if an item is in the list:
if "Latte" in new_list:
  print("Latte available")
else:
  print("Latte not available")
```

Now, lets have a look at the methods available for lists in Python.

# The methods of list objects

In this section, we will cover the methods available for the list data type in Python. Specifically, we will go through:

*   `list.undefined(x)`

*   `list.undefined(i, x)`

*   `list.undefined(iterable)`

*   `list.undefined(x)`

*   `list.undefined([i])`

*   `list.undefined()`

*   `list.undefined(x[, start[, end]])`

*   `list.undefined(x), list.undefined() & list.undefined()`

*   `list.undefined(undefined, undefined, undefined)`

## Adding elements

Let us assume we have an item x, that we want to add to a list. You can **append** (add to the end) an item to the list by using the\*\* **`list.undefined(x)` method. However, if you want to add an element to a desired position (for example, at the index i), the method** \*\*`list.undefined(i, x)` can be used. Keep in mind here that i is the index of the element before which to insert.

You can also extend a list by **appending** all the items in an \*iterable \*by using the method `list.undefined(iterable)`. Practice and clarify adding elements with the code below.

```
gloria_says = ["at", 1, "I"]
gloria_says.append("afraid,")

gloria_says.insert(3, "was")

gloria_also_says = ["I", "was", "petrified"]
gloria_says.extend(gloria_also_says)

print("Gloria says: ", gloria_says)
```

## Removing elements

Using the method `list.undefined(x)`, you can remove the first element from your list that has the value x. If there is no element with the value x, an exception (Value Error) is raised.

The `list.undefined([i])` takes an optional argument i, and removes the item with the index i from the list and return it. Note that the square brackets are there to denote that **i** is optional and they should not be entered. If this value is not specified, the last item is popped.

If you want to remove all items in the list, the method `list.undefined()` can be used.

```
my_list = ["dollop", "popple", "doohickey", "bumfuzzle", "bupkis"]

my_list.remove("bumfuzzle")
print(my_list)

device = my_list.pop(2)
print(device)
print(my_list)

my_list.clear()
print(my_list)
```

## Other methods

The method list.index(x\[, start\[, end]])can be used to obtain the index of the first item whose value is equal to x. Note that the index is zero based and that this method raises a ValueError if no such item exists. The arguments start and end are optional and can be used to limit the search to a subsequence of the list. These arguments are in the slice notation and we will discuss slicing in the next section.The returned index is computed relative to the beginning of the full sequence rather than the start argument.

*   `list.count(x)` will return how many times the item x appeared in the list.

*   `list.reverse()` can be used to reverse the elements in the list.

*   `list.copy()` creates a shallow copy of the list.

```
fruits = ['cherry', 'apple', 'banana', 'pear', 'kiwi', 'apple', banana']
fruits.count('banana')    # will return 2
fruits.index('apple', 3)  
```

*   `list.undefined(undefined, undefined, undefined)` sorts the items in the list (in ascending order by default). Here, **key** is an optional function that takes in one argument. This function is used to extract a comparison key from each element in the list. Check the example code below.

```
# a function used to return the length of an element
def getLength(e):
  return len(e)
  
inventory = ['Trident', 'Apple', 'Charcoal', 'Book']
inventory.sort(key=getLength)

print(inventory)

# This will return ['Book', 'Apple', 'Trident', 'Charcoal']
```

## List Slicing

Recall indexing that we discussed above. Slicing is similar, however it can return a sequence of items in a list, instead of just one item. When sliced using the `list[start:stop]` format, it will return items in the list from the *start* position until \*stop-1 \*position.

There is also the `list[start:stop:step]` format. This will will return items in the list from the *start* position until \*stop-1 \*position with the *step* used to skip items. Let us have a look at some examples.

Note that in some cases such as requesting for a number of items but the list contain lesser number of items than expected, Python will not throw an error. Instead, it will return what matches or an empty list.

If you do not specify *start*, items will be considered from the beginning. If *end* is not specified, from start until the end of the list will be considered. The default value for *step* is one. All three of these can take negative values too. Take a look at the examples below for clarity. You may also chose to try it out on your own.

```
inventory = ['Trident', 'Bone', 'Bow', 'Sword', 'Apple', 'Bread', 'Steak', 'Charcoal', 'Book', 'Bucket']

food = inventory[4:7]      # every item from index 4 until and not including index 7
weapons = inventory[:4]    # every item from begining untill and not including index 4
items = inventory[2::3]    # every third item, starting at index 2 till end of list 

# negative start or end values counts from the end of the array instead of the beginning
inventory[-1]      # the last item in the array
inventory[-2:]     # the last two items in the array: ['Book', 'Bucket']
inventory[:-2]     # everything except the last two items

# with a negative step
inventory[::-1]    # all items in the array, in reverse order
inventory[1::-1]   # the first two items, in reverse order: ['Bone', 'Trident']
inventory[:-3:-1]  # the last two items, in reverse order: ['Bucket', 'Book']
inventory[-3::-1]  # everything except the last two items, reversed: 
                   # ['Charcoal', 'Steak', 'Bread', 'Apple', 'Sword', 'Bow', 'Bone', 'Trident']
```

## List Comprehension

List comprehension provides users a way to concisely create a list.

A list comprehension contains within square brackets, an expression, which is followed by a `for` clause. This can also be followed by more `for` or `if` clauses. The result from this is a new list that will evaluate the expression in the context of the `for` and `if` clauses that follows. Let us look at some examples.

Creating a list of squares:

```
squares = []

```

This can be achieved more concisely using a single line of code using list comprehension:

```
squares = [x**2 
```

As you can see, this is more readable and concise.

Now let us take this a bit further. We want to compare two lists, and create a new list that combines elements if they do not match each other. Typically, you may write a code that looks like the one below.

```
new_list = []
list_a = [1, 2, 3, 4]
list_b = [1, 3, 2, 1]
```

List comprehension allows you to do this in a single line too.

```
new_list = [(x,y) 
```

You can also extend list comprehension to call a function on the elements in a list.

```
yell = [word.upper() 
```

# Other Useful Tips

Now that we discussed some important concepts, let us lastly have a look at some few tips that were not discussed.

We can create a new list with multiple similar multiple similar elements using the `my_list=[0] * 5` , which will create a list with 5 zeros \[0, 0, 0, 0, 0].

The `sort()` method we discussed in **The methods of the list object** section above, sorts the list in place. This changes the original list. To create a copy which is sorted and to leave the original list intact, the following method can be used: `new_list = sorted(mylist)`

You can concatenate two lists to form a new list with the last list appended to the first list.

```
list_a = [1, 2, 3] 
list_b = [4, 5, 6]new_list = list_a + list_b    # [1, 2, 3, 4, 5, 6]
```

## The del statement

If you want to delete an item from a list based on the **index**, the `del` statement can be used. This is different from the `pop()` method we discussed, which deleted and returned an item based on the **value**. The `del` statement can also be used to remove a sequence or to even clear the entire list.

```
list_a = [1, 2, 10, 30.05, 34.5]
```

## Copying a list

A note to keep in mind when you want to copy a list is, if you create a copy using assignment `copied_list = old_list` , modifying the `copied_list` will also change the `old_list`. This is because with the = assignment used here, both lists refer to the same list inside the memory and no new list is created. Therefore, be extremely careful in such assignments.

An actual copy can be created using

```
new_list = old_list.copy()
```

Another way to do this is

```
new_list = list(old_list)
```

Also can be done with slicing

```
new_list = old_list[:]
```

# Summary

In this in depth guide, we looked at Python lists, how to create them, built-in methods you can use. We also looked at some concepts such as slicing and list comprehension, which can help make your code more concise and readable. We finished off with some useful tips and notes to keep in mind when working with lists. In future guides, we will continue to look at other Python concepts. So stay tuned.

Feel free to practice with the code snippets used in this guide, because you can only improve your programming skills with practice!
