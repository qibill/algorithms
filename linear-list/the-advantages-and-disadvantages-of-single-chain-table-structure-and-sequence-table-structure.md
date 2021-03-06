# 单链表结构与顺序存储结构的优缺点

### 时间性能

#### -查找

* 顺序存储结构  O\(1\)
* 单链表  O\(n\)

#### -插入和删除

* 顺序存储结构需要平均移动表一半的元素，时间为 O\(n\)
* 单链表在计算出某位置的指针后，插入和删除时间仅为 O\(1\)

### 空间性能

* 顺序存储结构需要分配存储空间，分大了，容易造成空间浪费，分小了，容易发生溢出。
* 单链表不需要分配存储空间，只要有就可以分配，元素个数也不受限制。

#### 经验结论

* 若线性表需要频繁查找，很少进行插入和删除操作是，宜采用顺序存储结构。
* 若需要频繁插入和删除时，宜采用单链表结构。

#### 实际

* 用户注册的个人信息，除了注册是插入数据外，绝大多数情况都是读取，所以考虑用顺序存储结构。
* 玩家的武器或者装备列表，随着游戏过程中，可能随时增加或删除，所以考虑单链表结构。



