---
layout: post
title:  "HashMap&HashTable&HashSet"
date:   2020-09-15 23:25:00
categories: Java
---

#### HashMap HashTable HashSet总结   

>Hashmap vs Hashtable
>>HashSet 是Set接口的实现，**不允许重复值**  
>>最主要的是，存储在HashSet中的对象必须重写equals()进行相等性检查，而hashCode()方法中没有重复值的存储在我们的集合中  
>>
>>HashMap是Map Interface的实现，该映射将键映射到值。映射中**不允许使用重复键**  
>>Hashmap是一个数组和链表的结合体（在数据结构称“链表散列“）.HashMap允许空值和空键  
>>
>>HashSet和HashMap都不同步  

>Hashmap vs Hashtable:
>>1. HashMap不同步。它不是线程安全的，没有适当的同步代码就无法在许多线程之间共享,而Hashtable是同步的。它是线程安全的，可以与许多线程共享  
>>2. HashMap中，null可以作为键，这样的键只有一个,可以有一个或多个键所对应的值为null;而Hashtable不允许任何空键或值  
>>3. 如果不需要线程同步，通常首选HashMap而不是HashTable  


参考：
* [HashMap HashTable HashSet区别剖析总结]
* [Differences between HashMap and HashTable in Java]
* [Difference between HashMap and HashSet]

[HashMap HashTable HashSet区别剖析总结]:https://blog.csdn.net/jianyuerensheng/article/details/51593118
[Differences between HashMap and HashTable in Java]:https://www.geeksforgeeks.org/differences-between-hashmap-and-hashtable-in-java/
[Difference between HashMap and HashSet]:https://www.geeksforgeeks.org/difference-between-hashmap-and-hashset/