---
title: Depth First Search (DFS)
---
# Depth-first Tree Traversal

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

We can traverse trees or graphs in many orders.  Depth-first traversal is a very common tree traversal pattern. For some problems, it's more appropriate than breadth-first search.

### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- Describe and draw depth-first tree traversal.
- Compare and contrast depth-first and breadth-first.
- Pseudocode depth-first search.
- Identify use cases for depth-first search.

### Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- Explain tree terms: root, node, edge/branch, leaf, parent, child.
- Describe and/or draw breadth-first traversal.
- Follow the flow of recursive functions.

# Depth-first Search

Depth-first traversal traverses (goes over) every node in a graph.  Depth-first search is an algorithm that searches through (potentially) every node in a graph. Like with Breadth-first search, we can search for many keys, search by criteria that aren't based on keys, and keep track of depth.

**Depth-first search chooses a start node and "visits" all the nodes in the graph by following each path as far (as deep) as it can before going to the next path.**  In a tree, we pick the root as the start node (surprise!).

Depth-first search follows an "always go left" or "always go right" path like some people use to systematically solve mazes.

<img alt="depth-first search animation" src="https://upload.wikimedia.org/wikipedia/commons/7/7f/Depth-First-Search.gif" width="40%">

Breadth-first search used a queue (first in is first out) to keep track of which nodes to visit next.  Depth-first search, in its iterative form, uses a stack (first in is last out).  Depth-first search can be done recursively, too. The iterative version translates more easily to graphs that might have looping paths (after you see both versions, think about why that is).

### Depth-first Traversal

Here's a rundown of depth-first tree traversal:

1. Set up a stack to track which nodes to visit.

1. Add the root to the stack.

1. Until the stack is empty, process the top node in the stack with the following steps:
	- pop the node from the top of the stack
	- push the node's children onto the top of the stack
	- do whatever additional processing you'd like!

Or, a recursive approach:

1. If a node has no children (base case), just process the node itself.  

2. If a node has children (recursive case), recursively traverse each child's subtree in a depth-first way.  When all of the children are finished, process the node.

#### Check for Understanding

1. Draw the stack at each step in depth-first traversal for the tree below:

  ![img](img/tree.jpg)

<details><summary>Answer</summary>
[D]

[D, B]


[D, B, A]


[D, B]


[D, B, C]


[D, B]


[D]


[D, F]

	
[D, F, E]

	
[D, F]

	
[D]

	
[]


No more nodes
</details>