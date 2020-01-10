## HashSet

作为Set接口主要实现类，线程不安全，可以存储null

#### 1、存储

当向HashSet集合存入一个元素时,HashSet会调用该对象的hashCode()方法的到，根据hashcode值计算出该对象在HashSet中的位置（Hash算法存储集合元素，较高的查找和存储性能）

- hashCode()值相同,会调用equals方法，返回true则添加失败，返回false则链起来
- equals方法相同 只要hascode不同，就认为是不同的对象（相等的对象必须具有相等的散列值）

#### 2、理解

​	无序性：放置元素并非按照索引添加元素，而是按照hascode值来添加索引

​	不可重复性：相同的元素只能添加一次

​	底层：JDK7使用数组+链表		JDK8使用HashMap

## LinkedHashSet

#### 1、存储

​	既使用Hashcode值来决定元素的位置，又使用双向链表维护元素的顺序，看起来是按照添加顺序保存的。

​	添加性能略低与HashSet，良好的迭代性能

​	不允许有重复的元素

## TreeSet（只能添加相同的类型）

SortedSet接口的实现类，保证集合元素处于有序状态

#### 1、存储

红黑数存储数据，不允许有相同的元素

#### 2、实现

必须实现comparable接口，重写compareTo方法作为TreeSet判断两个对象是否相等的标准

- ​	自然排序：compareTo（T o）
- ​    定制排序：compareTo（T o1，T o2）

