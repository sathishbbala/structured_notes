In Python a set is used to store a collection like lists, tuples, dictionaries with different qualities and usage. A set is a collection which is unordered, unchangeable, and unindexed.
1. Set items are unchangeable but an item can be removed and a new item can be added.
2. Set is unordered so the items can appear in a different order every time it is used.
3. Set does not allow duplicate values. It automatically removes any duplicate entries.
4. In a set the values True and 1 are considered duplicates. Similarly 0 and False are also considered duplicates.
5. An item in a set can contain a string, integer, or a boolean data types.
6. A set() constructor is used to initialize a set
``` python
set_a = {"Zomato", "Swiggy", "Zepto", "Instamart", "Blinkit"}
set_b = {1,2,3,4,5}
set_c = {"Raman", "Artificial Intelligence", 89, True}
```
7. Items in a set cannot be accessed using an index or a key. Use a for loop to access individual items in a set.
``` python
for element in set_a:
  print(element)
```
8. To check if an item exists in a set or not, use the following syntax:
``` python
set_b = {1,2,3,4,5]
print(6 in set_b)
print(6 not in set_b)
```
9. Add an item to a set using the add method
``` python
set_b = {1,2,3,4,5}
set_b.add(6)
```
10. update method is used to add items to a set. Note that object joining does not need to be a set but can be a tuple, list or a dict. From a dict, each key and value becomes an item in the set.
    The update() method modifies the original set and does not create a new set. 
``` python
set_a = {"Zomato", "Swiggy", "Zepto", "Instamart", "Blinkit"}
set_c = {"Raman", "Artificial Intelligence", 89, True}
set_a.update(set_c)
print(set_a)

list_a = ["Rishi", "ML", 90, False]
set_a.update(list_a)
print(set_a)

tuple_a = (19,24,56)
set_a.update(tuple_a)
print(set_a)

dict_a = { "june": 79,
           "july": 90,
           "august": 91
           }
set_a.update(dict_a)
print(set_a)
set_a = {"Zomato", "Swiggy", "Zepto", "Instamart", "Blinkit"}
set_c = {"Raman", "Artificial Intelligence", 89, True}
set_a.update(set_c)
```
11. Remove or discard method is used to remove an item from a set. The remove method will raise an error if the item does not exist while discard does not raise an error.
12. pop method can be used to remove an item from a set but this method will remove a random item and return the removed item.
13. The clear method empties a set while del keyword will delete the set.
14. There are several ways to join two or more sets in Python:
    - The union() and update() methods joins all items from both sets.
    - The '|' operator can be used to instead of union().
    - The union() method takes multiple sets as input.
    - The union() method allows a list or a tuple to be joined with the resulting set. 
    - The intersection() method keeps ONLY the duplicates.
    - The '&' operator can be used instead of intersection().
    - The difference() method keeps the items from the first set that are not in the other set(s).
    - The symmetric_difference() method keeps all items EXCEPT the duplicates. This will remove an item from the set only if the same item is in other set.

* Frozenset will include later



