# <a href="top"></a>Binary Tree
- [Back to Main Page](https://github.com/PdxCodeGuild/career-guide)

Definition: A **binary tree** is a **tree** where every node has two or fewer children. The children are usually called left and right.

```Python
class BinaryTreeNode(object):

  def __init__(self, value):
      self.value = value
      self.left  = None
      self.right = None
```

This lets us build a structure like this:

  ![a perfect tree](../resources/binary_tree/perfect_tree.PNG)

That particular example is special because every level of the tree is completely full. There are no "gaps". We call this kind of tree "perfect".

Binary trees have a few interesting properties when they're perfect:

**Property 1: the number of total nodes on each "level" doubles as we move down the tree.**

  ![a perfect tree](../resources/binary_tree/doubles.PNG)

**Property 2: the number of nodes on the last level is equal to the sum of the number of nodes on all other levels (plus 1)**. In other words, about _half_ of our nodes are on the last level.

Let's call the number of nodes _n_, and the height of the tree _h_. _h_ can also be thought of as the "number of levels".

If we had _h_, how would we calculate _n_.

Let's just add up the number of nodes on each level! How many nodes are on each level?

If we zero-index the levels, the number of nodes on the xxth level is exactly 2<sup>x</sup>.

1. Level 0: 2<sup>0</sup> nodes
2. Level 1: 2<sup>1</sup> nodes
3. Level 2: 2<sup>2</sup> nodes
4. Level 3: 2<sup>3</sup> nodes
5. etc

So our total number of nodes is:

n = 2<sup>0</sup> + 2<sup>1</sup> + 2<sup>2</sup> + 2<sup>3</sup> + ... + 2<sup>h-1</sup>

> Why only up to 2<sup>h-1</sup>? Notice that we started counting our levels at 0. So if we have h levels in total, the last level is actually the "h-1h-1"-th level. That means the number of nodes on the last level is 2<sup>h-1</sup>.

But we simplify. Property 2 tells us that the number of nodes on the last level is (1 more than) half of the total number of nodes, so we can just take the number of nodes on the last level, multiply it by 2, and subtract 1 to get the number of nodes overall. We know the number of nodes on the last level is 2<sup>h-1</sup>, so:

n = 2<sup>h-1</sup> * 2 - 1

n =2<sup>h-1</sup> * 2<sup1</sup> - 1

n =2<sup>h-1+1</sup> - 1

n =2<sup>h-1+1</sup> - 1

n = 2<sup>h</sup> - 1

So what's how we can go from _h_ to _n_. What about the other direction?

We need to bring _h_ to _n_. That's what logs are for!

First, some quick review, log<sub>10</sub>(100) simply means, **"What power must you raise 10 in more to get 100?"** Which is 2, because 10<sup>2</sup> = 100.

We can use logs in algebra to bring variables down from exponents by exploiting the fact that we can simplify log<sub>10</sub>(10<sup>2</sup>). What power must we raise 10 in order to get 10<sup>2</sup>? Easy, it's 2.

So, in this case we can take log<sub>2</sub> of both sides:

n = 2<sup>h</sup> -1

n + 1 = 2<sup>h</sup>

log<sub>2</sub> ((n+1)) = log<sub>2</sub> (2<sup>h</sup>)

log<sub>2</sub> (n+1) = h

So that's the relationship between height and total nodes in a perfect binary tree.

[Back to top](#top)
