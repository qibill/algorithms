### 题目

> 小明的女朋友最喜欢在网上买买买了，可是钱包里钞票有限，不能想买啥就买啥。                         
>
> 面对琳琅满目的物品，她想买尽可能多的种类，每种只买一件，同时总价格还不能超过预算上限。                  
>
> 于是她请小明写程序帮她找出应该买哪些物品，并算出这些物品的总价格。

### 输入规范

> 每个输入包含两行。第一行是预算上限。第二行是用空格分隔的一组数字，代表每种物品的价格。所有数字都为正整数并且不会超过10000。

### 输出规范：

> 对每个输入，输出应买物品的总价格。

### 例子

> 输入示例1:                   
>
> 100                      
>
> 50 50                    
>
> 输出示例1:                   
>
> 100                      
>
>                          
>
> 输入示例2:                   
>
> 188                      
>
> 50 42 9 15 105 63 14 30  
>
> 输出示例2:                   
>
> 160

---

## 

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

public class test2 {
    public static void main (String[] args) {
        Scanner scanner = new Scanner(System.in);
        String line = scanner.nextLine();
        int money = Integer.parseInt(line);
        line = scanner.nextLine();
        List<Integer> list = new ArrayList<>();
        String[] strings = line.split(" ");
        for (String string : strings) {
            list.add(Integer.parseInt(string));
        }
        Collections.sort(list);
        
        int sum = 0;
        for (Integer i : list) {
            if ((sum + i)> money) {
                break;
            }
            sum += i;       
        }
        System.out.println(sum);
    }
}
```



