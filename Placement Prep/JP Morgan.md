## 1) Milk Delivery

``import java.util.*;
public class milkman {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n=sc.nextInt();

        int m=sc.nextInt();

        PriorityQueue<int []> arr=new PriorityQueue<>((a,b)->a[0]-b[0]);

        for(int i=0;i<n;i++) {

            int [] temp={sc.nextInt(),sc.nextInt()};

            arr.add(temp);

        }

        int ans=0;

        int[] prev=arr.poll();

        while(!arr.isEmpty()){

            int[] curr=arr.poll();

            if(prev[1]>=curr[0]){

                prev=new int[]{prev[0],Math.max(prev[1],curr[1])};

            }

            else{  

                ans+=(prev[1]-prev[0]);

                prev=curr;

            }

        }

        ans+=(prev[1]-prev[0]);

        System.out.println("Answer is = "+ans);

    }

}

 //  O(n * log(n)) due to the priority queue operations, where n is the number of elements in the input list.`


## 2) Wooden Chair

`import java.util.*;
`public class chair {
  ``  public static void main(String[] args) {
    ``    Scanner sc = new Scanner(System.in);
      ``  int n = sc.nextInt();
        ``int[] arr = new int[n];
        fo`r(int i=0; i<n; i++) {
            a`rr[i] = sc.nextInt();
        }`
        in`t[] great = new int[n];
        int[`] less = new int[n];
        Arra`ys.fill(great,-1);
        Array`s.fill(less,-1);
        for(int` i=0; i<n; i++){
            for(in`t j=i+1; j<n; j++){
                if(ar`r[j] > arr[i]){
                    `if(great[i]==-1){  
                      ``  great[i] =  j;
                    }`
                }`
                if(`arr[j] < arr[i]){
                    i`f(less[i] == -1){
                       `` less[i] = j;
                    }`
                }`
                if(`great[i]!=-1 && less[i]!=-1){
                    `break;
                }`
            }`
        }`
        in`t s = 0;
        for`(int i=0; i<n; i++){
            if`(great[i] != -1 && less[great[i]] != -1){
                `s += 5;
            }els`e if(great[i] != -1 && less[great[i]] == -1){
                s `+= 10;
            }else `if(great[i] == -1){
                s +`= 15;
            }`
        }`
        Sy`stem.out.println(s);
    }`
}``
``
