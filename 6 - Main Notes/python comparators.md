

2025-06-06 09:03

Status:

Tags: [[dsa comparators]] [[dsa sorting]] [[python]] [[pythonic code]]


# python comparators

Comparator Function: A **comparator function** is a function that defines how two elements are compared during sorting.

## List comparators example
```python
arr = [[2, 5], [0, 5], [1, 5], [3, 0]]

# Sort on the basis of the second element
arr1 = sorted(arr, key= lambda x: x[1]) # output [[3, 0], [2, 5], [0, 5], [1, 5]]
print(arr1)

# Sort in reverse order on the basis of second element
arr2 = sorted(arr, key= lambda x: -x[1]) # output [[2, 5], [0, 5], [1, 5], [3, 0]]
print(arr2)

# Sort on 2nd element and then 1st element
arr3 = sorted(arr, key= lambda x: (x[1], x[0])) # output [[3, 0], [0, 5], [1, 5], [2, 5]]
print(arr3)

# Given an shopping items order list, sort them
list_of_orders = ['#53', '#7', '#3356', '#19', '#17185']

def orders_sorting(string):
    return int(string[1:])

sorted_by_number = sorted(list_of_orders, key=orders_sorting)
print(sorted_by_number) # output ['#7', '#19', '#53', '#3356', '#17185']

# Sorting a list of dicts (sort pokemon by pokedex)
list_of_pokemon = [
    {
        "name": "Squirtle",
        "pokedex": 7,
        "type": "water"
    },
    {
        "name": "Bulbasaur",
        "pokedex": 1,
        "type": "grass"
    },
    {
        "name": "Charmander",
        "pokedex": 4,
        "type": "fire"
    }
]

def sort_by_pokedex(pokemon):
    return pokemon["pokedex"]

print(sorted(list_of_pokemon, key=sort_by_pokedex))
```

# Dict Comparator examples
```python
# Return a dict which is sorted by values
fruits_preference = {
    "mango": 1,
    "banana": 4,
    "cheku": 3
}

print(dict(sorted(fruits_preference.items(), key=lambda item: item[1])))
```
**Breakdown:**

- `fruits.items()`
	- Returns a view of the dictionary’s items as `(key, value)` pairs.
- `sorted(fruits.items())`: By default, it sorts based on key.
- `sorted(fruits.items(), key=lambda item: item[1])`
	- Sorts these `(key, value)` pairs by the value `item[1]`
	- The `lambda item: item[1]`is a function that takes each `(key, value)` tuple and returns the value for sorting.
    
- `dict(...)` 
	- Converts the sorted list of tuples back into a dictionary.  
	- Since Python 3.7+, the insertion order is preserved, so the resulting dictionary is sorted by values.





# References
