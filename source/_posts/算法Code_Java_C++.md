---
title: 剑指Offer算法Code_Java_C++
date: 2018-07-16 09:39:40
tags: [Java, C++]
---

剑指Offer算法Code_Java_C++

<!--more-->

在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
>思路：从左下角元素往上查找，右边元素是比这个元素大，上边是的元素比这个元素小。
Java代码
```
public class Solution {
    public boolean Find(int target, int [][] array) {
        //填写
        int row = array.length;
        int col = array[0].length;
        int i=row-1,j=0;
        while(i>=0&&j<=col-1){
            if(target<array[i][j]){
                i--;
            }else if(target>array[i][j]){
                j++;
            }else
                return true;
        }
        return false;
    }
}
```
C++代码
```
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        // array是二维数组，这里没做判空操作
        int rows = array.size();
        int cols = array[0].size();
        int i=rows-1,j=0;//左下角元素坐标
        while(i>=0 && j<cols){//使其不超出数组范围
            if(target<array[i][j])
                i--;//查找的元素较少，往上找
            else if(target>array[i][j])
                j++;//查找元素较大，往右找
            else
                return true;//找到
        }
        return false;
    }
};
```

----
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。
Java代码：
```
public class Solution {
    public String replaceSpace(StringBuffer str) {
    	String str1 = str.toString();
        String str2 = str1.replace(" ","%20");
        return str2;
    }
}
```
Java代码：
```
public class Solution {
    public String replaceSpace(StringBuffer str) {
        int spacenum = 0;//spacenum为计算空格数
        for(int i=0;i<str.length();i++){
            if(str.charAt(i)==' ')
                spacenum++;
        }
        int indexold = str.length()-1; //indexold为为替换前的str下标
        int newlength = str.length() + spacenum*2;//计算空格转换成%20之后的str长度
        int indexnew = newlength-1;//indexold为为把空格替换为%20后的str下标
        str.setLength(newlength);//使str的长度扩大到转换成%20之后的长度,防止下标越界
        for(;indexold>=0 && indexold<newlength;--indexold){ 
                if(str.charAt(indexold) == ' '){  //
                str.setCharAt(indexnew--, '0');
                str.setCharAt(indexnew--, '2');
                str.setCharAt(indexnew--, '%');
                }else{
                    str.setCharAt(indexnew--, str.charAt(indexold));
                }
        }
        return str.toString();
    }
}
```

c++代码
```
class Solution {
public:
	void replaceSpace(char *str,int length) {
    int count = 0;
        for (int i=0;i<length;i++){
            if (str[i]==' '){
                count++;
            }
            for (int i=length-1;i>=0;i--){
                if (str[i]==' '){
                    count--;
                  str[i+2*count]='%';
                str[i+2*count+1]='2';
                str[i+2*count+2]='0';
                }else{
                      str[i+2*count]=str[i];
                }
            }
        }
	}
};
```
---
输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。

Java代码：
```
java 递归超简洁版本
public class Solution {
    ArrayList<Integer> arrayList=new ArrayList<Integer>();
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        if(listNode!=null){
            this.printListFromTailToHead(listNode.next);
            arrayList.add(listNode.val);
        }
        return arrayList;
    }
}
```
C++代码
```
class Solution {
public:
    vector<int> printListFromTailToHead(ListNode* head) {
        vector<int> value;
        if (head != NULL){
            value.insert(value.begin(),head->val);
            while (head->next !=NULL){
                value.insert(value.begin(),head->next->val);
                head = head ->next;
            }
        }
        return value;
    }
};
```
---
输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。
>递归思想，每次将左右两颗子树当成新的子树进行处理，中序的左右子树索引很好找，前序的开始结束索引通过计算中序中左右子树的大小来计算，然后递归求解，直到startPre>endPre||startIn>endIn说明子树整理完到。方法每次返回左子树活右子树的根节点
```
      1
     /  \
   2     3
  /\    /
 4  5  6
  \    /
   7  8
```
Java代码：
```
public class Solution {
    public TreeNode reConstructBinaryTree(int [] pre,int [] in) {
        TreeNode root=reConstructBinaryTree(pre,0,pre.length-1,in,0,in.length-1);
        return root;
    }
    //前序遍历{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}
    private TreeNode reConstructBinaryTree(int [] pre,int startPre,int endPre,int [] in,int startIn,int endIn) {
         
        if(startPre>endPre||startIn>endIn)
            return null;
        TreeNode root=new TreeNode(pre[startPre]);
         
        for(int i=startIn;i<=endIn;i++)
            if(in[i]==pre[startPre]){
                root.left=reConstructBinaryTree(pre,startPre+1,startPre+i-startIn,in,startIn,i-1);
                root.right=reConstructBinaryTree(pre,i-startIn+startPre+1,endPre,in,i+1,endIn);
                      break;
            }
                 
        return root;
    }
}
```

---
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0）。
n<=39

Java代码
```
public class Solution {
    public int Fibonacci(int n) {
        if(n<1){
            return n;
        }
        int[] ints = new int[n+1];
        ints[0] = 0;
        ints[1] = 1;
        
        for(int i = 2; i <= n; i++ ){
            ints[i] = ints[i-1] + ints[i-2];
        }
        return ints[n];
    }
}
```
C++代码：
```
class Solution {
public:
    int Fibonacci(int n) {
    int pre = 0;
        int last=1;
            int result =0;
        if(n<=1){
            return n;
        }
        for(int i=2; i<=n; i++){
            result=pre+last;
            pre=last;
            last=result;
        }
        return result;
    }
};
```

---

一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。
>思路：，f(1) = 1, f(2) = 2, f(3) = 3, f(4) = 5，  可以总结出f(n) = f(n-1) + f(n-2)的规律
Java代码：
```
public class Solution {
    public int JumpFloor(int target) {
        int[] ints= new int[target+1];
        if(target <=0 ){
            return 0;
        }else if(target==1 || target==2){
            return target;
        }
        ints[0] = 1;ints[1] = 2;
        for(int i =2; i<=target; i++){
            ints[i] = ints[i-1] + ints[i-2];
           }
        return ints[target-1];
    }
}
```
C++代码
```
class Solution {
public:
    int jumpFloor(int number) {
        int first = 1;int second = 2; int result = 0;
        if (number<=0){
            return 0;
        }else if (number==1||number==2){
            return number;
        }
        for (int i=3; i<=number; i++){
            result = first + second;
            first = second;
            second = result;
        }
        return result;
    }
};
```

---
输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。
>思路：1自身左移动，然后跟原数字做**与**比较，如果对应相同输出为1，否则为0。
Java代码：
```
public class Solution {
    public int NumberOf1(int n) {
    int count = 0;
        int flag = 1;
        while(flag != 0){
            if((n & flag) !=0 ){
                count++;
            }
            flag = flag << 1;
        }
        return count;
    }
}
```

C++代码：
```
class Solution {
public:
     int  NumberOf1(int n) {
         int count = 0;
         int flag = 1;
         while(flag != 0){
             if((n & flag)!=0){
                 count++;    
             }
             flag = flag << 1;
         }
        return count   ;  
     }
    
};
```
---

输入一个链表，反转链表后，输出新链表的表头:
>整体反转链表，但是要把断开的节点保存起来，才能继续反转链表
Java代码： 
```
public class Solution {
    public ListNode ReverseList(ListNode head) {
       
        if(head==null)
            return null;
        //head为当前节点，如果当前节点为空的话，那就什么也不做，直接返回null；
        ListNode pre = null;
        ListNode next = null;
        //当前节点是head，pre为当前节点的前一节点，next为当前节点的下一节点
        //需要pre和next的目的是让当前节点从pre->head->next1->next2变成pre<-head next1->next2
        //即pre让节点可以反转所指方向，但反转之后如果不用next节点保存next1节点的话，此单链表就此断开了
        //所以需要用到pre和next两个节点
        //1->2->3->4->5
        //1<-2<-3 4->5
        while(head!=null){
            //做循环，如果当前节点不为空的话，始终执行此循环，此循环的目的就是让当前节点从指向next到指向pre
            //如此就可以做到反转链表的效果
            //先用next保存head的下一个节点的信息，保证单链表不会因为失去head节点的原next节点而就此断裂
            next = head.next;
            //保存完next，就可以让head从指向next变成指向pre了，代码如下
            head.next = pre;
            //head指向pre后，就继续依次反转下一个节点
            //让pre，head，next依次向后移动一个节点，继续下一次的指针反转
            pre = head;
            head = next;
        }
        //如果head为null的时候，pre就为最后一个节点了，但是链表已经反转完毕，pre就是反转后链表的第一个节点
        //直接输出pre就是我们想要得到的反转后的链表
        return pre;
    }
}
```

C++代码：
```
class Solution {
public:
    ListNode* ReverseList(ListNode* pHead) {

        if(pHead == NULL){
            return NULL;
        }
        
        ListNode* pNode = pHead;//当前指针
        ListNode* pPre = NULL;//链表的前一个指针
        ListNode* pNewHead = NULL;
        
        while(pNode != NULL){
           ListNode* pNext = pNode->next;
            if(pNext == NULL){ //尾节点
                pNewHead = pNode;
            }
            pNode->next = pPre;
            pPre = pNode;
            pNode = pNext;
        }
        return pNewHead;
    }
};
```
---
输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。
>两两数值对比

Java代码：

C++代码：

---


Java代码：

C++代码：
---


Java代码：

C++代码：
---


Java代码：

C++代码：
---


Java代码：

C++代码：
---


Java代码：

C++代码：
---


Java代码：

C++代码：
---


Java代码：

C++代码：
---


Java代码：

C++代码：