![[Pasted image 20240325090241.png]]

![[Pasted image 20240325090312.png]]

`import java.util.*;`
`public class breakapalindrome {`
    `public static void main(String[] args) {`
        `Scanner sc=new Scanner(System.in);`
        `String str = sc.nextLine();`
        `String ans=breakpalindromefun(str);`
        `System.out.println(ans);`
    `}`
    `public static String breakpalindromefun(String s) {`
        `int a_count=0;//to count the a occurences`
        `if(s.length()==1) return "IMPOSSIBLE";//it is impossible to perform the replacement? Only when the length = 1.`
        `for(int i=0;i<s.length();i++){`
            `char ch=s.charAt(i);`
            `if(ch!='a'){`
                `s=s.substring(0,i)+"a"+s.substring(i+1,s.length());`
                `if(!pan(s)){`
                    `return s;`
                `}`
                `s=s.substring(0,i)+ch+s.substring(i+1,s.length());`
            `}`
            `a_count++;`
        `}`
        `if(a_count==s.length()){`
            `s=s.substring(0,s.length()-1)+'b';`
        `}`
        `return s;`
    `}`
    `public static boolean pan(String s){`
        `int i=0;`
        `int j=s.length()-1;`
        `while(i<=j){`
            `if(s.charAt(i)!=s.charAt(j)){`
                `return false;`
            `}`
            `i++;`
            `j--;`
        `}`
        `return true;`
    `}`
`}`
Change the first non 'a' character to 'a'.
What if the string has only 'a'?
Change the last character to 'b'.

## No Pair Allowed:

![[Pasted image 20240325105243.png]]

`import java.util.*;`
`public class no_pair_allowed {`
    `public static int tell(String s) {`
        `int count = 0;`
        `int temp = 1;`
        `int len = s.length();`
        `char ch = s.charAt(0);`
        `for (int i = 1; i < len; i++) {`
            `if (ch == s.charAt(i)) {`
                `temp++;`
            `} else {`
                `count += (temp / 2);`
                `temp = 1;`
                `ch = s.charAt(i);`
            `}`
        `}`
        `count += (temp / 2);`
        `return count;`
    `}`
    `public static void main(String[] args) {`
        `Scanner sc = new Scanner(System.in);`
        `int n = sc.nextInt();`
        `Vector<String> v = new Vector<>();`
        `for (int i = 0; i < n; i++) {`
            `v.add(sc.next());`
        `}`
        `for (String i : v) {`
            `System.out.println(tell(i));`
        `}`
        `sc.close();`
    `}`
`}`

![[Pasted image 20240325133549.png]]

`import java.util.Scanner;`
`public class growthdimension {`
    `public static void main(String[] args) {`
        `Scanner sc = new Scanner(System.in);`
        `int n = sc.nextInt();`
        `int first = sc.nextInt();`
        `int second = sc.nextInt();`
        `for (int i = 1; i < n; i++) {`
            `int a = sc.nextInt();`
            `int b = sc.nextInt();`
            `first = Math.min(first, a);`
            `second = Math.min(second, b);`
        `}`
        `System.out.println(first * second);`
        `sc.close();`
    `}`
`}`

