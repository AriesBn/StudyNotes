# Map

1. ##### HashMap（LinkedHashMap）、TreeMap、Hashtable（Properties）

2. key无序不可重复，set存储所有的key（keySet方法），key所在的类必须重写equals和hashcode方法

3. Entry无序不可重复，set存储所有的Entry（entrySet方法），key-value构成一个Entry

4. vaule无序可重复，collection存储所有的value（.values得到collection），value所在的类重写equals方法



#### HashMap

​	Map接口的主要实现类，效率高，线程不安全，可以存储null

​	底层实现：JDK7数组+链表  JDK8之后使用数组+链表+红黑树

​	方法：

1. put(key,value)<添加与修改>
2. remove(key)
3. get(key)<得到value by key> 
4. size()大小
5. Map与Set的结合

#### LinkedHashMap

​	HashMap基础上使用了双向链表来记录添加的元素的顺序，迭代顺序与添加的顺序一致

​	

#### TreeMap

使得所有的key-value处于有序状态，底层使用红黑树

key排序：

1. 自然排序实现Comparable接口重写compareTo方法
2. 自然排序实现Comparator接口重写compare方法

判断两个对象相等的标准变成了重写的compareTo和compare方法是否返回0



