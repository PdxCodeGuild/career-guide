
# <a href="top"></a>Data Structures

## Table of Contents
- [Random Access Memory (RAM)](#random)
- [Binary Numbers](#binary)
- [Fixed-Width Integers](#fixed)
- [Arrays](#arrays)
- [Strings](#strings)
- [Pointers](#pointers)
- [Dynamic Arrays](#dynamic)
- [Linked Lists](#linked)
- [Hash Tables](#hash)

### <a href="random"></a>Random Access Memory (RAM)

When a computer is running code, it needs to keep track of variables. Those variables are store in **random access memory** (**RAM**). RAM can be referred to "working memory" or just "memory".

RAM is separate from **storage**. While **memory** is where we keep the variables our functions allocate as they crunch data for us, **storage** is where we keep files.

**Memory (or RAM)** is faster but has less space, while storage (or "disc") is slower but has more space. A modern laptop might have ~500 GB of storage but only ~16 GB if RAM.

[Back to top](#top)

### <a href="binary"></a>Binary Numbers
- [Binary Numbers Explained – Beginners Guide](http://www.steves-internet-guide.com/binary-numbers-explained/) by Steves Internet Guide (article)
- [Binary Numbers and Base Systems](https://www.youtube.com/watch?v=LpuPe81bc2w) by Techquickie (video)

[Back to top](#top)

### <a href="fixed"></a>Fixed-Width Integers

Most integers are fixed-width or fixed-length, which means the number of bits they take up doesn't change.

It's usually safe to assume an integer is fixed-width unless you're told otherwise. Variable-size numbers exist, but they're only used in special cases.

If we have a 64-bit fixed-length integer, it doesn't matter if that integer is 0 or 193,457—it still takes up the same amount of space in RAM: 64 bits.

In big O notation, we say fixed-width integers take up constant space or O(1) space.

And because they have a constant number of bits, most simple operations on fixed-width integers (addition, subtraction, multiplication, division) take constant time (O(1) time).

So fixed-width integers are very space efficient and time efficient.

But that efficiency comes at a cost—their values are limited. Specifically, they're limited to 2<sup>n</sup>
possibilities, where n is the number of bits.

So there's a tradeoff. As we'll see, that's a trend in data structures—to get a nice property, we'll often have to lose something.

[Back to top](#top)

### <a href="arrays"></a>Arrays

Arrays have fast lookups (O(1) time), but each item in the array needs to be the same size, and you need a big block of uninterrupted free memory to store the array.

[Back to top](#top)
### <a href="string"></a>Strings

Definition: A series of characters (letters, punctuation, etc.). To store characters, we use a mapping system called character encoding, ASCII. Here's how the alphabet is encoded in ASCII with binary numbers.

![character encoding](./resources/data_structures/character-encoding.PNG)

[Back to top](#top)

### <a href="pointers"></a>Pointers

Instead of storing the strings right inside our array, let's just put the strings wherever we can fit them in memory. Then we'll have each element in our array hold the address in memory of its corresponding string. Each address is an integer, so really our outer array is just an array of integers. We can call each of these integers a pointer, since it points to another spot in memory.

This fixes both the disadvantages of arrays:

1. The items don't have to be the same length—each string can be as long or as short as we want.

2. We don't need enough uninterrupted free memory to store all our strings next to each other—we can place each of them separately, wherever there's space in RAM.

But the pointers in this array make it not cache-friendly, because the baby names are scattered randomly around RAM. So reading from the 0th index, then the 1st index, etc. doesn't get that extra speedup from the cache.

That's the tradeoff. This pointer-based array requires less uninterrupted memory and can accommodate elements that aren't all the same size, but it's slower because it's not cache-friendly.

> This slowdown isn't reflected in the big O time cost. Lookups in this pointer-based array are still O(1) time.

[Back to top](#top)

### <a href="dynamic"></a>Dynamic Arrays
 Definition: an array that's programed to resize itself when it runs out of space

 > Python, Ruby, and JavaScript use dynamic arrays for their default array-like data structures. In Python, they're called "lists." Other languages have both. For example, in Java, array is a static array (whose size we have to define ahead of time) and ArrayList is a dynamic array.

 The advantage of dynamic arrays over arrays is that you don't have to specify the size ahead of time, but the disadvantage is that some appends can be expensive. That's the tradeoff.

[Back to top](#top)
### <a href="linked"></a>Linked Lists

These quick appends and prepends for linked lists come from the fact that linked list nodes can go anywhere in memory. They don't have to sit right next to each other the way items in an array do.

So the tradeoff with linked lists is they have faster prepends and faster appends than dynamic arrays, but they have slower lookups.

[Back to top](#top)
### <a href="hash"></a>Hash Tables

But that's sort of the tradeoff with hash tables. You get fast lookups by key...except some lookups could be slow. And of course, you only get those fast lookups in one direction—looking up the key for a given value still takes O(n)O(n) time.

[Back to top](#top)

### Summary
Arrays have O(1)-time lookups. But you need enough uninterrupted space in RAM to store the whole array. And the array items need to be the same size.

But if your array stores pointers to the actual array items (like we did with our list of baby names), you can get around both those weaknesses. You can store each array item wherever there's space in RAM, and the array items can be different sizes. The tradeoff is that now your array is slower because it's not cache-friendly.

Another problem with arrays is you have to specify their sizes ahead of time. There are two ways to get around this: dynamic arrays and linked lists. Linked lists have faster appends and prepends than dynamic arrays, but dynamic arrays have faster lookups.

Fast lookups are really useful, especially if you can look things up not just by indices (0, 1, 2, 3, etc.) but by arbitrary keys ("lies", "foes"...any string). That's what hash tables are for. The only problem with hash tables is they have to deal with hash collisions, which means some lookups could be a bit slow.

Each data structure has tradeoffs. You can't have it all.

So you have to know what's important in the problem you're working on. What does your data structure need to do quickly? Is it lookups by index? Is it appends or prepends?

Once you know what's important, you can pick the data structure that does it best.

[Back to top](#top)
