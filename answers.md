# CMPS 2200 Assignment 5
## Answers

**Name:
Mohini Yadav**





- **1a
- logdn**


- **1b
- Delete min: Each steps costs O(d) work and the heap depth is O(logdN), so the total work is: O(d x logdN)
- For an insert operation, the each step costs O(1) and the heap depth is O(log dN) and the total work is O(logdN)
**


- **1c
- Log base is d. The work bound is O(d logd|v|) for delete-min operations, and since there are |V| delete-min operations, the total time for delete-min is O(|V| x dlogd |V|).Insert operations or decrease operations take O(logd|V|) time. Because there are as many as |E| insert/ decrease operations, the total time for insertion is: O(|E| x logd |V|). So the overall work bound is O(|V| x dlogd |V| +|E| x logd|V|).**

- **1d.
- The value of d which results in this is:  d = Θ(log |V|)
 **


- **2a.
- The APSP(i,j,k) for all i,j,k is:
  APSP(0,0,-1) = 0
APSP(0,1,-1) = -2
APSP(0,2,-1) = 2
APSP(1,0,-1) = ∞
APSP(1,1,-1) = 0
APSP(1,2,-1) = 1
APSP(2,0,-1) = ∞
APSP(2,1,-1) = ∞
APSP(2,2,-1) = 0

APSP(0,0,0) = 0
APSP(0,1,0) = -2
APSP(0,2,0) = 2
APSP(1,0,0) = ∞
APSP(1,1,0) = 0
APSP(1,2,0) = 1
APSP(2,0,0) = ∞
APSP(2,1,0) = ∞
APSP(2,2,0) = 0

APSP(0,0,1) = 0
APSP(0,1,1) = -2
APSP(0,2,1) = -1
APSP(1,0,1) = ∞
APSP(1,1,1) = 0
APSP(1,2,1) = 1
APSP(2,0,1) = ∞
APSP(2,1,1) = ∞
APSP(2,2,1) = 0


APSP(0,0,2) = 0
APSP(0,1,2) = -2
APSP(0,2,2) = -1
APSP(1,0,2) = ∞
APSP(1,1,2) = 0
APSP(1,2,2) = 1
APSP(2,0,2) = ∞
APSP(2,1,2) = ∞
APSP(2,2,2) = 0
- **


- **2b.
- The relationship between APSP(i,j,1) and APSP(i,j,2) is that APSP(i,j,2) is the minimum of both APSP(i,j,1) and APSP(i,2,1)+ APSP(2,j,1). This is because the relationship between the shortest path from using only vertices 0 or 1 is the same as the path from only using vertices 0, 1, 2, similarly you can go between vertices 2 to j or i to 2, in both cases you are only using vertices 0 and 1. **


- **2c
- The optimal substructure property for APSP(i,j,k) is that APSP(i,j,k) consists of the minimum of APSP(i,j,k-1) and APSP(i,k,k-1) + APSP(k,j,k-1). I computed the shortest path from i to j by allowing intermediate nodes which are all less than or ewual to k, which factors that the best path either doesnt involve k, so it is the same as APSP(i,j,k-1) or that the best path involves going through k and is equal to k, in which case the best path is the path from i to k plus the best path from k to j. **

- **2d.
  Using top-down memoization, ywe compute each subproblem from scratch only one time and then consistently keep the result in the table for future use. This gives us a number of distinct subproblems = n x n x n = n^3 where n is the number of vertices in the graph. The resulting work of this dynamic programming algorithm is 0(n^3) since each subproblem requires only O(1) or constant time work by looking at the table submissions. **

- **2e.
- The work is O(n^3) for this algorithm, when comparing this algorithm work with the work of Johnsons algorithm which has a work of O(n^2logn +nE) where E is the amount of edges in the graph. If the graph is ddense, which means that the number of edges is rougly the same as n^2, (E = N^2), then Johnsons aglorithm runs in O(n^3) which is when dynamic programming algorithm programs are preferable. IIf the graph is sparse, however, meaning that E << n^2, Johnson's algorithm is much faster- closer to O(n^2/log n), making the Johnsons algorithm preferable to the dynamic programming algorithm. **



- **3a.
- A solution to the MST problem is not always promised to be a solution to a MMET problem. This is because the MST minimizes the sum of all edges, while the MMET minimizes the maximum signle edge weight in the three. These two not always guarantee to solve each other because they have different goals. To explain this further, there is an edge case in which an MST includes a heavy edge because it has a goal of reducing the total weight, but MMET would try to avoid any heavt edge even if the total sum is a little larger. Because these two algorithms have different optimization goals, this leads to different solutions being presented in certain cases.**


- **3b.
- If the MST is unavailable, we ae able to find the next best spanning tree using this algorithm:
- 1. Use the Prims or Jruskals algorithm to find the optimal MST
  2. For each edge E in the MST:
     - remove the e from the MST, this will split the tree into two components
     - Find the minimum weight edge that connects these two components among all the edges that are not already included in the MST
     - Form a new spanning tree by replacing e with the minimum weight edge
     - Record the total weight of the new tree created
  3. After checking all the edges e in the MST, select the replacement tree which has the smallest total weight**


- **3c.
- Work analysis of this algorithm:
- n is the number of vertices, and m is the number of edges.
- Making the original MST takes O(mlog n) time by using Kruskals algorithm. And for each n-1 edge of the MST:
  Removing an edge splits the MST into two components, and then finding the lightest edge connecting the two components can take O(m) time. Therefore, we do O(m) work for each of the O(n) edges, So the total work AFTER building the MST is O(mn). Therefore the total work is O(m logn +mn). 
- **
