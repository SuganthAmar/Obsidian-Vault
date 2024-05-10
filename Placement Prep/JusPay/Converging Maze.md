### Largest Sum Cycle

You are given a maze with N cells. Each cell may have multiple
entry points but not more than one exit (ie. entry/exit points
are unidirectional doors like valves).

The cells are named with an integer value from 0 to N-1.

You have to find:

The sum of the largest sum cycle in the maze. Return -1 if there
are no cycles.

1. Sum of a cycle is the sum of the node number of all nodes in
that cycle.

INPUT FORMAT :

1. The first line has the number of cells N.
2. The second line has a list of N values of the edge[] array.
`edge[i]` contains the cell number that can be reached from of
cell 'i' in one step. `edge[i]` is -1 if the i’th cell 

OUTPUT FORMAT :

The first line denotes the sum of the largest sum cycle.
Sample Input and Output
Input :
1
23
4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21
Output :
45

```java
package JusPay;
import java.util.*;
public class Max_Cycle {
    static int maxi=-1;
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] edges = new int[n];
        for (int i = 0; i < n; i++) {
            edges[i] = sc.nextInt();
        }
        int ans=maxWeight(edges);
        System.out.println(ans);
        sc.close();
    }
        public static int maxWeight(int[] edges){
            int n=edges.length;
            boolean[] vis=new boolean[n];
            int ans=0;
            for(int i=0;i<n;i++){
                if(!vis[i]){
                    Map<Integer, Integer> dist = new HashMap<>();
                    dist.put(i,1);
                    dfs(i,vis,edges,dist);
                }
            }
            return maxi;
        }
        public static void dfs(int ind,boolean[] vis,int[] edges,Map<Integer, Integer> dist){
            vis[ind]=true;
            int nind=edges[ind];
            if(nind!=-1 && !vis[nind]){
                dist.put(nind,dist.get(ind)+edges[nind]);
                dfs(nind,vis,edges,dist);
            }
            else if(nind!=-1 && dist.containsKey(nind)){
                maxi=Math.max(maxi,dist.get(ind)-dist.get(nind)+edges[nind]);
            }
        }
    }
```

- Time Complexity: O(n^2)
- Space Complexity: O(n)

### Nearest meeting cell 
Problem Description
You are given a maze with N cells. Each cell may have multiple
entry points but not more than one exit
(i.e. entry/exit points are unidirectional doors like valves).
The cells are named with an integer value from 0 to N-1.
You have to find:
Nearest meeting cell:
Given any two cells - C1, C2, find the closest cell Cm that can be
reached from both C1 and C2.
Function Description:
You are given a function Solution containing arr[N], src, desc as
inputs.
Complete the code in the function and return the answer from
it.

INPUT FORMAT

1. An integer T, denoting the number of testcases, followed by
3T lines, as each testcase will contain 3 lines.
2. The first line of each testcase has the number of cells N
3. The second line of each testcase has a list of N values of the
edge[] array. edge[i] contains the cell number that can be
reached from cell 'i' in one step. edge[i] is -1 if the 'i'th cell
doesn't have an exit.
4. Third line for each testcase contains two cell numbers whose
nearest meeting cell needs to be found. (return -1 if there is no
meeting cell from the two given cells)

OUTPUT FORMAT
For each testcase given, output a single line that denotes the
nearest meeting cell (NMC)
Sample Input & Output
Input
1
23
4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21
9 2

Output
4

```java
package JusPay;
import java.util.*;
public class Common_Node {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] edges = new int[n];
        for (int i = 0; i < n; i++) {
            edges[i] = sc.nextInt();
        }
        int x=sc.nextInt();
        int y=sc.nextInt();
        System.out.println(maxWeight(edges,x,y));
        sc.close();
    }
    public static int maxWeight(int[] edges,int x,int y){
        int n=edges.length;
        boolean[] vis=new boolean[n];
        int ans=0;
        while(x!=-1 && y!=-1){
            if(vis[x]){
                ans=x;
                break;
            }
            else if(vis[y]){
                ans=y;
                break;
            }
            vis[x]=true;
            vis[y]=true;
            x=edges[x];
            y=edges[y];
        }
        return ans;
    }
}
```

- Time Complexity (TC): O(n)
- Space Complexity (SC): O(n)

### Maximum Weight Node

Problem Description

You are given a maze with N cells. Each cell may have multiple
entry points but not more than one exit (ie. entry/exit points
are unidirectional doors like valves).

The cells are named with an integer value from 0 to N-1.

You have to find:

Find the node number of maximum weight node (Weight of a
node is the sum of node numbers of all nodes pointing to that
node)

INPUT FORMAT

1. An integer T, denoting the number of testcases, followed by
2T lines, as each testcase will contain 2 lines.
2. The first line of each testcase has the number of cells N.
3. The second line of each testcase has a list of N values of the
edge[] array. edge[i] contains the cell number that can be
reached from of cell 'i' in one step. edge[i] is -1 if the 'i'th cell
doesn't have an exit.

OUTPUT FORMAT
First line denotes the node number with maximum wight
node.
Sample Input
1
23
4 4 1 4 13 8 8 8 0 8 14 9 15 11 -1 10 15 22 22 22 22 22 21

Sample Output
22

```java
package JusPay;
import java.util.*;
public class Max_weight_Node {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] edges = new int[n];
        for (int i = 0; i < n; i++) {
            edges[i] = sc.nextInt();
        }
        System.out.println(maxWeight(edges));
        sc.close();
    }
    public static int maxWeight(int[] edges){
        int n=edges.length;
        int[] indeg=new int[n];
        int ans=0;
        for(int i=0;i<n;i++){
            if(edges[i]!=-1){
                indeg[edges[i]]++;
            }
        }
        int maxIndex = 0;
        int maxValue = indeg[0];
        for (int i = 1; i < indeg.length; i++) {
            if (indeg[i] > maxValue) {
                maxValue = indeg[i];
                maxIndex = i;
            }
        }
        return maxIndex;
    }
}
```

- Time Complexity (TC): O(n)
- Space Complexity (SC): O(n)
