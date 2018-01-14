### 题目

> 李雷和韩梅梅坐前后排，上课想说话怕被老师发现，所以改为传小纸条。为了不被老师发现他们纸条上说的是啥，他们约定了如下方法传递信息：
>
> 将26个英文字母（全为大写），外加空格，一共27个字符分成3组，每组9个。也就是ABCDEFGHI是第一组，JKLMNOPQR是第二组，STUVWXYZ\*是第三组（此处用\*代表空格）。
>
> 然后根据传递纸条那天的日期，改变字母的位置。
>
> 先根据月份数m，以整个分组为单位进行循环左移，移动\(m-1\)次。
>
> 然后根据日期数d，对每个分组内的字符进行循环左移，移动\(d-1\)次。
>
> 以3月8日为例，首先移动分组，3月需要循环左移2次，变成：
>
> STUVWXYZ\*，ABCDEFGHI，JKLMNOPQR
>
> 然后每组内的字符，8日的话需要循环左移7次，最终的编码为：
>
> Z\*STUVWXY，HIABCDEFG，QRJKLMNOP
>
> 对于要传递信息中的每个字符，用组号和组内序号两个数字来表示。
>
> 如果在3月8日传递信息“HAPPY”，那么H位于第2组的第1个，A位于第2组第3个，P位于第3组第9个，Y位于第1组第9个，所以纸条上会写成：
>
> 21 23 39 39 19
>
> 现在给定日期和需要传递的信息，请输出应该写在纸条上的编码。

### 输入规范

> 每个输入包含两行。第一行是用空格分隔的两个数字，第一个数字是月份，第二个数字是日子。输入保证是一个合法的日期。
>
> 第二行为需要编码的信息字符串，仅由A~Z和空格组成，长度不超过1024个字符。

### 输出规范：

> 对每个输入，打印对应的编码，数字之间用空格分隔，每个输出占一行。

### 例子

> 输入示例1:
>
> 1 1
>
> HI
>
> 输出示例1:
>
> 18 19
>
>
>
> 输入示例2:
>
> 3 8
>
> HAPPY
>
> 输出示例2:
>
> 21 23 39 39 19
>
>
>
> 输入示例3:
>
> 2 14
>
> I LOVE YOU
>
> 输出示例3:
>
> 35 25 18 12 29 31 25 23 12 28

---

### 

```java
import java.util.Scanner; 

public class test1 {                                           

    public static void main(String[] args) {                   
        //读取输入的数据                                              
        Scanner scanner = new Scanner(System.in);              
        String line = scanner.nextLine();                      
        String[] strings = line.split(" ");                    
        int month = Integer.parseInt(strings[0]);              
        int day = Integer.parseInt(strings[1]);                
        line = scanner.nextLine();                             

        char[] c1 = "ABCDEFGHI".toCharArray();                 
        char[] c2 = "JKLMNOPQR".toCharArray();                 
        char[] c3 = "STUVWXYZ ".toCharArray();                 

        CycleLinkList<Character> cl1 = new CycleLinkList<>();  
        CycleLinkList<Character> cl2 = new CycleLinkList<>();  
        CycleLinkList<Character> cl3 = new CycleLinkList<>();  

        for (char c : c1) {                                    
            CNode<Character> node = new CNode<>();             
            node.setData(c);                                   
            cl1.addCNode(node);                                
        }                                                      

        for (char c : c2) {                                    
            CNode<Character> node = new CNode<>();             
            node.setData(c);                                   
            cl2.addCNode(node);                                
        }                                                      

        for (char c : c3) {                                    
            CNode<Character> node = new CNode<>();             
            node.setData(c);                                   
            cl3.addCNode(node);                                
        }                                                      

        CycleLinkList<CycleLinkList<Character>> cl4 = new Cycle

        CNode<CycleLinkList<Character>> node1 = new CNode<>(); 
        CNode<CycleLinkList<Character>> node2 = new CNode<>(); 
        CNode<CycleLinkList<Character>> node3 = new CNode<>(); 
        node1.setData(cl1);                                    
        node2.setData(cl2);                                    
        node3.setData(cl3);                                    

        cl4.addCNode(node1);                                   
        cl4.addCNode(node2);                                   
        cl4.addCNode(node3);                                   

        for (int i = 0; i < month - 1; i++) {                  
            cl4.head = cl4.head.getNextCNode();                
        }                                                      
        for (int i = 0; i < day - 1; i++) {                    
            cl1.head = cl1.head.getNextCNode();                
            cl2.head = cl2.head.getNextCNode();                
            cl3.head = cl3.head.getNextCNode();                
        }                                                      

        char[] chars = line.toCharArray();                     
        for (char c : chars) {                                 
            for (int i = 1; i <= cl4.size; i++) {              
                CNode<CycleLinkList<Character>> index = cl4.ind
                CycleLinkList<Character> data = index.getData()
                for (int j = 1; j <= data.size; j++) {         
                    CNode<Character> node = data.index(j);     
                    Character character = node.getData();      
                    if(character.equals(c))                    
                    System.out.print("" + i + j + " ");        
                }                                              
            }                                                  
        }                                                      
    }                                                          

}                                                              

class CycleLinkList<E> {                                       

    CNode<E> head;//头指针                                        
    CNode<E> current;//当前结点对象                                  
    int size;//结点个数                                            

    //初始化一个空链表                                                 
    public CycleLinkList()                                     
    {                                                          
        //初始化头结点，让头指针指向头结点。并且让当前结点对象等于头结点。                     
        this.head = current = new CNode<E>();                  
        this.size = 0;//单向链表，初始长度为零。                           
        this.head.setNextCNode(this.head);                     
    }                                                          

    public void addCNode(CNode<E> node) {                      
        if(size == 0) {                                        
            this.head = current = node;                        
            this.head.setNextCNode(this.head);                 
        }else {                                                
            current.setNextCNode(node);                        
            current = node;                                    
            current.setNextCNode(head);                        
        }                                                      
        size++;                                                
    }                                                          

    public CNode<E> index(int i) {                             
        CNode<E> node = head;                                  
        for (int j = 0; j < i - 1; j++) {                      
            node = node.getNextCNode();                        
        }                                                      
        return node;                                           
    }                                                          
}                                                              
class CNode<E> {                                               

    private E data; // 定义数据域                                   
    private CNode<E> nextCNode; // 定义下一个节点                     

    public E getData() {                                       
        return data;                                           
    }                                                          

    public void setData(E data) {                              
        this.data = data;                                      
    }                                                          

    public CNode<E> getNextCNode() {                           
        return nextCNode;                                      
    }                                                          

    public void setNextCNode(CNode<E> nextCNode) {             
        this.nextCNode = nextCNode;                            
    }                                                          
}
```



