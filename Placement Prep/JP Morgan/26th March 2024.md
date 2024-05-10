[Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

**Input:** s = "the sky is blue"
**Output:** "blue is sky the"

Program:

`class Solution {`
    `public String reverseWords(String s) {`
        `String[] str=s.split(" +");`//this + also consider the additional spaces too
        `StringBuilder ans=new StringBuilder();`
        `for(int i=str.length-1;i>=0;i--){`
            `ans.append(str[i]);`
            `ans.append(" ");`
        `}`
        `return ans.toString().trim();`
    `}`
`}`
//TC:->O(n)
//SC:->O(n)
Time 8:20 -> 8.25am

 [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)

`class Solution {`
    `public void solveSudoku(char[][] board) {`
        `if(sudoku(board,0,0)){`
            `return;`
        `}`
    `}`
    `public boolean place(char[][] b,int i,int j,int val){`
        `//check for that row`
        `for(int row=0;row<b[0].length;row++){`
            `if(b[i][row]==(char)(val+'0')){`
                `return false;`
            `}`
        `}`
        `//check for that column`
        `for(int col=0;col<b.length;col++){`
            `if(b[col][j]==(char)(val+'0')){`
                `return false;`
            `}`
        `}`
        `//checking for the grid so we need to find the start row and col pos of a 3x3 grid starting of a grid is always a multiple of 3`
        `i=i-(i%3);//i=5 i=>3`
        `j=j-(j%3);//j=7 j=>6`
        `for(int pi=0;pi<3;pi++){`
            `for(int pj=0;pj<3;pj++){`
                `if(b[pi+i][pj+j]==(char)(val+'0')){`
                    `return false;`
                `}`
            `}`
        `}`
        `return true;`
    `}`
    `public boolean sudoku(char[][] b,int i,int j){`
        `if(i==b.length) {`
            `return true;`
        `}`
        `int ni=j==8?i+1:i;//just move the pointer to the next row first pos after a complete pass`
        `int nj=j==8?0:j+1;//just moves the pointer to the next row first pos after a complete pass`
        `if(b[i][j]=='.'){`
            `for(int val=1;val<=9;val++){`
                `if(place(b,i,j,val)){`
                    `b[i][j]=(char)(val+'0');`
                    `if(sudoku(b,ni,nj)){`
                        `return true;`
                    `}`
                    `b[i][j]='.';`
                `}`
            `}`
        `}`
        `else{`
           `if(sudoku(b,ni,nj)){`
               `return true;`
           `}`
        `}`
        `return false;`
    `}`
`}`
TC:->O(9^(n^2))
SC:->O(1)
## Shortest Path in the Unit Weight unidirected graph:
`import java.util.*;`
`public class shortpath {`
    `public static void main(String[] args) {`
        `Scanner sc=new Scanner(System.in);`
        `int e=sc.nextInt();`
        `int v=sc.nextInt();`
        `int s=sc.nextInt();`
        `int d=sc.nextInt();`
        `int[][] edeges=new int[e][2];`
        `for(int i=0;i<e;i++){`
            `edeges[i][0]=sc.nextInt();`
            `edeges[i][1]=sc.nextInt();`
        `}`
        `int[] ans=fun(edeges,v,e,s,d);`
        `for(int it:ans){`
            `System.out.print(it+" ");`
        `}`
    `}`
    `public static int[] fun(int[][] edges, int n,int m, int src, int dest) {`
        `// Create an adjacency list of size N for storing the undirected graph.`
        `ArrayList<ArrayList<Integer>> adj = new ArrayList<>();`
        `for (int i = 0; i < n; i++) {`
            `adj.add(new ArrayList<>());`
        `}`
        `for (int i = 0; i < m; i++) {`
            `adj.get(edges[i][0]).add(edges[i][1]);`
            `adj.get(edges[i][1]).add(edges[i][0]);`
        `}`
        `// A dist array of size N initialized with a large number to`
        `// indicate that initially all the nodes are untraversed.`
        `int dist[] = new int[n];`
        `// A parent array to store the parent node of each node.`
        `int parent[] = new int[n];`
        `for (int i = 0; i < n; i++) {`
            `dist[i] = (int) 1e9;`
            `parent[i] = -1; // Initialize parent array with -1 (indicating no parent).`
        `}`
        `dist[src] = 0;`
        `// BFS Implementation`
        `Queue<Integer> q = new LinkedList<>();`
        `q.add(src);`
        `while (!q.isEmpty()) {`
            `int node = q.poll();`
            `for (int it : adj.get(node)) {`
                `if (dist[node] + 1 < dist[it]) {`
                    `dist[it] = 1 + dist[node];`
                    `parent[it] = node; // Update parent of the current node.`
                    `q.add(it);`
                `}`
            `}`
        `}`
        `// Constructing the path from destination to source`
        `ArrayList<Integer> path = new ArrayList<>();`
        `int current = dest;`
        `while (current != -1) { // Until source is reached (source has no parent).`
            `path.add(current);`
            `current = parent[current];`
        `}`
        `// Reverse the path to get source to destination order`
        `Collections.reverse(path);`
        `// Updated shortest distances are stored in the resultant array ‘ans’.`
        `// Unreachable nodes are marked as -1.`
        `int[] ans = new int[path.size()];`
        `for (int i = 0; i < path.size(); i++) {`
            `ans[i] = path.get(i);`
        `}`
        `return ans;`
    `}`
`}`
//TC:->O(E+V);
//SC:->O(E);

[Happy Number](https://leetcode.com/problems/happy-number/)

`class Solution {`
    `public boolean isHappy(int n) {`
        `String s=Integer.toString(n);`
        `while(s.length()>1){`
            `int sum=0;`
            `for(int i=0;i<s.length();i++){`
                `sum+=Math.pow(Character.getNumericValue(s.charAt(i)),2);`
            `}`
            `s=Integer.toString(sum);`
        `}`
        `if(s.equals("1")||(s.equals("7"))){`
            `return true;`
        `}`
       `else{`
            `return false;`
        `}`
    `}`
`}`
//TC:-> O(n)
//SC:-> O(1)

[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

`class Solution {`
    `public boolean isValid(String s) {`
        `Stack<Character> stack = new Stack<Character>(); // create an empty stack`
        `for (char c : s.toCharArray()) { // loop through each character in the string`
            `if (c == '(') // if the character is an opening parenthesis`
                `stack.push(')'); // push the corresponding closing parenthesis onto the stack`
            `else if (c == '{') // if the character is an opening brace`
                `stack.push('}'); // push the corresponding closing brace onto the stack`
            `else if (c == '[') // if the character is an opening bracket`
                `stack.push(']'); // push the corresponding closing bracket onto the stack`
            `else if (stack.isEmpty() || stack.pop() != c) // if the character is a closing bracket`
                `// if the stack is empty (i.e., there is no matching opening bracket) or the top of the stack`
               `// does not match the closing bracket, the string is not valid, so return false`
                `return false;`
        `}`
        `// if the stack is empty, all opening brackets have been matched with their corresponding closing brackets,`
        `// so the string is valid, otherwise, there are unmatched opening brackets, so return false`
        `return stack.isEmpty();`
    `}`
`}`

//TC:=> O(n)
//SC:=> O(n).

## Flip Bits
`int count=0;`
        `char ch='1';`
        `for(int i=0;i<s.length();i++){`
            `if(ch=='1'){`
                `count++;`
                `ch=(char)(48+(ch+1)%2);`
            `}`
        `}`
        `return count++;`
`//TC :=> O(n)`

[Minimum Swaps to Make Strings Equal](https://leetcode.com/problems/minimum-swaps-to-make-strings-equal/)

`class Solution {`
    `public int minimumSwap(String s1, String s2) {`
        `if(s1.length() != s2.length()) return -1;`
        `int n = s1.length();`
        `int x = 0 , y = 0;`
        `for(int i = 0 ; i < n ; i ++){`
            `char c1 = s1.charAt(i) , c2 = s2.charAt(i);`
            `if(c1 == 'x' && c2 == 'y') x++;`
            `else if(c1 == 'y' && c2 == 'x') y++;`
        `}`
        `if(x % 2 == 0 && y % 2 == 0) return x/2 + y/2;`
        `else if(x % 2 == 1 && y % 2 == 1) return x/2 + y/2 + 2;`
        `return -1;`
    `}`
`}`

//O(n)-> TC
