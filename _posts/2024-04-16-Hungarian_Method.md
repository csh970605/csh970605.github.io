---
title: Hungarian Method
author: SeHoon
date: 2024-04-16 10:02:30 +0900
categories: [Papers, DeepLearning]
tags: [Papers, DeepLearning, MultiObjectTracking]
math: true
mermaid: true
---

# [Hungarian Method](https://sites.math.washington.edu/~thomas/teaching/m514_web/50YearsIP.pdf#page=46)


The Hungarian method is an algorithm for efficiently solving an assignment problem. The assignment problem involves efficiently distributing multiple resources to multiple tasks, such as assigning employees to projects or machines to tasks.
<br><br><br><br>

# Steps of the Hungarian Method

Assume that a cost matrix consists of $n \times n$ elements. Each row represents a resource, and each column represents a task. The objective of the Hungarian Method is to assign each resource to exactly one task while minimizing overall costs. To assign well, there are 6 steps:

1. Prepare a cost matrix : Find the minimum cost for each resource in the original cost matrix, subtract this minimum value from each row, and adjust it. This ensures that each row has at least one zero.

2. Reduce columns : After reducing the rows, find the minimum value in each column and subtract it from all elements in that column. This will also give each column at least one zero.

3. Covering and assignment of zeros : Find the maximum set of independent zeros in the adjusted cost matrix and assign each zero to one resource and one task. This process often leads to an optimal assignment; otherwise, further adjustments are required.

4. Line Draw : Use the minimum number of horizontal and vertical lines needed to cover all zeros. The minimum number of lines used in this step must match the size (n) of the cost matrix.

5. Matrix Adjustment : Find the minimum value of any elements not covered by a line. Subtract this minimum value from all positions not covered by a line, leave it unchanged in the positions covered by a line, and add it to the positions covered by two lines.

6. Repeat : Repeat this process until all resources are assigned to tasks.

# Example

Assume that there is a cost matrix:

| | Task A | Task B | Task C |
|---|---|---|---|
| resource 1 | 4 | 1 | 3 |
| resource 2 | 2 | 0 | 5 |
| resource 3 | 5 | 3 | 4 |

Follow the steps above:

1. Reduce rows:

    + Minimum value of resource 1 = 1. $\rightarrow$ [3, 0, 2]
    
    + Minimum value of resource 2 = 0. $\rightarrow$ [2, 0, 5]

    + Minimum value of resource 3 = 3. $\rightarrow$ [2, 0, 1]

    The resulting matrix is:


    | | Task A | Task B | Task C |
    |---|---|---|---|
    | resource 1 | 3 | 0 | 2 |
    | resource 2 | 2 | 0 | 5 |
    | resource 3 | 2 | 0 | 1 |


2. Reduce columns:

    + Minimum value of task A = 2. $\rightarrow$ [1, 0, 0]

    + Minimum value of task A = 0. $\rightarrow$ [0, 0, 0]

    + Minimum value of task A = 1. $\rightarrow$ [1, 5, 0]

    The resulting matrix is:



    | | Task A | Task B | Task C |
    |---|---|---|---|
    | resource 1 | 1 | 0 | 0 |
    | resource 2 | 0 | 0 | 0 |
    | resource 3 | 1 | 5 | 0 |


Now, we can assign resource 1 to Task B, resource 2 to Task A, and resource 3 to Task C.

Note that if the cost matrix is:



| | Task A | Task B | Task C |
|---|---|---|---|
| resource 1 | 0 | 0 | 0 |
| resource 2 | 0 | 0 | 0 |
| resource 3 | 1 | 5 | 0 |

we can assign tasks as we want, such as assigning resource 1 to Task A, resource 2 to Task B, and resource 3 to Task C.