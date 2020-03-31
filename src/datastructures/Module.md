A linked list is a linear collection of data elements, whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a collection of nodes which together represent a sequence. In its most basic form, each node contains: data, and a reference (in other words, a link) to the next node in the sequence.

# Module Overview

This module provides a doubly linked list implementation with its operations. Operations that index into the list will traverse the list from the beginning or the end, whichever is closer to the specified index.
Note that this implementation is not synchronized. If multiple threads access a linked list concurrently, and at least one of the threads modifies the list structurally, it must be synchronized externally.

## Compatibility
|                    | Version      |
|:------------------:|:------------:|
| Ballerina Language | 1.2.0        |

## API Guide

First, import the `ldclakmal/linkedlist` module into the Ballerina project.

```ballerina
import ldclakmal/datastructures as ds;
```

Now, initialize the LinkedList object as follows:

```ballerina
ds:LinkedList list = new;
```

All the APIs with documentation can be found below:

```ballerina
# Returns the first element in this list.
#
# + return - Value of the head of the list, of `()` if the list is empty
public function getFirst() returns anydata;
```

```ballerina
# Returns the last element in this list.
#
# + return - Value of the tail of the list, of `()` if the list is empty
public function getLast() returns anydata;
```

```ballerina
# Return the element at the specified index, if index is valid.
#
# + index - Index of the list, starting from 0
# + return - Value of the element or `()` if the list is empty or index is invalid
public function getByIndex(int index) returns anydata;
```

```ballerina
# Inserts the specified element at the beginning of this list.
#
# + value - Value to be inserted
public function addFirst(anydata value);
```

```ballerina
# Appends the specified element to the end of this list.
#
# + value - Value to be inserted
public function addLast(anydata value);
```

```ballerina
# Appends the specified element to the specified index of the list.
#
# + value - Value to be inserted
# + index - Index of the list, starting from 0
public function addByIndex(anydata value, int index);
```

```ballerina
# Removes and returns the first element from this list.
#
# + return - Value of the first element or `()` if the list is empty
public function removeFirst() returns anydata;
```

```ballerina
# Removes and returns the last element from this list.
#
# + return - Value of the last element or `()` if the list is empty
public function removeLast() returns anydata;
```

```ballerina
# Removes the specified element from this list, if it is present.
#
# + value - Value to be removed
public function remove(anydata value);
```

```ballerina
# Removes the element at the specified index from this list, if index is valid.
#
# + index - Index of the list, starting from 0
# + return - Value of the removed element or `()` if the list is empty or index is invalid
public function removeByIndex(int index) returns anydata;
```

```ballerina
# Returns true if this list contains the specified element.
#
# + value - Value to be checked for
# + return - `true` if the list contains the specified, `false` otherwise
public function contains(anydata value) returns boolean;
```

```ballerina
# Return the size (no of elements) of the list.
#
# + return - The size of the list
public function size() returns int;
```

```ballerina
# Removes all of the elements from this list.
public function clear();
```

```ballerina
# Prints the complete linked list with head and tail in following pattern.
# '[HEAD] 6 -> 2 -> 1 -> 4 -> 5 [TAIL]'
#
# + return - The string representation of the complete linked list
public function print() returns string;
```

## Examples

```ballerina
import ballerina/io;
import ballerina/test;
import ldclakmal/datastructures as ds;

public function main() {
    ds:LinkedList list = new;
    list.addFirst(1);
    list.addFirst(2);
    list.addFirst(3);
    int last = <int>list.removeLast();
    test:assertEquals(last, 1);
    list.addLast(4);
    list.addLast(5);
    int first = <int>list.removeFirst();
    test:assertEquals(first, 3);
    list.addFirst(6);
    list.addLast(7);
    list.remove(5);
    first = <int>list.getFirst();
    test:assertEquals(first, 6);
    last = <int>list.getLast();
    test:assertEquals(last, 7);
    boolean contains = list.contains(7);
    test:assertTrue(contains);
    contains = list.contains(1);
    test:assertFalse(contains);
    int get = <int>list.getByIndex(2);
    test:assertEquals(get, 4);
    list.addByIndex(10, 2);
    int remove = <int>list.removeByIndex(2);
    test:assertEquals(remove, 10);

    string actual = list.print();
    string expected = "[HEAD] 6 -> 2 -> 4 -> 7 [TAIL]";
    test:assertEquals(actual, expected);
    test:assertEquals(list.size(), 4);
}
```
