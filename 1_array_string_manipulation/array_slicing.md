# Array Slicing
- [Back to Main Page](https://github.com/PdxCodeGuild/career-guide)

**Array slicing** involves taking a subset from an array and **allocating a new array with those elements**.

In Python 2.7, you can create a new list of the elements in my_list, from start_index to end_index (exclusive), like this:
```Python2.7
my_list[start_index:end_index]
```

You can also get everything from start_index onwards by just omitting end_index

```Python2.7
my_list[start_index:]
```

**Careful: there's a hidden time and space cost here!** It's tempting to think of slicing as just "getting elements", but in reality you are:

1. allocating a new list
2. _copying_ the elements from the original list to the new list

This takes O(n) time and O(n) space, where _n_ is the number of elements in the _resulting_ list.
