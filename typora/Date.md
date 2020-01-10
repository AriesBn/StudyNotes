```java
java.util.Date
System.currentTimeMillis();date.getTime() 获取毫秒数
常用构造器：1无参直接打印Date实例 2有参构造器传毫秒  获取日期

java.sql.Date得到的日期比较常用
java.sql.Date date2=new java.sql.Date(new Date().getTime()); util获得毫秒使用sql的构造器
sql Date唯一的构造函数

simpleDateFormat类
构造器
SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
之后格式化和解析就可以按照这个格式来

1.日期到文本  格式化
SimpleDateFormat simpleDateFormat = new SimpleDateFormat();
Date date = new Date();
String format = simpleDateFormat.format(date);
System.out.println(format);

2.文本到日期 记得抛出解析异常
String string="19-8-17 上午9:49";
Date parse = simpleDateFormat.parse(string);
System.out.println(parse);

```

```java
java.util.Calendar;抽象类

1.get方法:
Calendar calender = Calendar.getInstance(); 实例化的方法
System.out.println(calender.get(Calendar.DAY_OF_MONTH));
					实例	   get  	      静态属性	
2.set方法:
System.out.println(calender.get(Calendar.DAY_OF_WEEK));			//周六 结果为7
calender.set(Calendar.DAY_OF_WEEK, 2);
System.out.println(calender.get(Calendar.DAY_OF_WEEK));			//结果为2

3.add方法
因为修改的是本实例，所以一定要加calender.add
calender.add(Calendar.DAY_OF_WEEK, 3);							//结果为5

4.getTime方法得到日期类，而且得到的是修改后的日期   	Calendar类-->Date类
本来日期为2019-08-17 10:30:31
得到结果为2019-08-15 10:30:31
Date date=calender.getTime();
String format = simpleDateFormat.format(date);		//与simpleDateFormat结合使用
System.out.println(format);										

5.setTime方法得到日历类，将时间变回来					Date类-->Calendar类

calender.setTime(new Date());
System.out.println(calender.get(Calendar.DAY_OF_WEEK));

```

```java
因为偏移量的问题，java8提供java.time等新的包

```

### Instant

```java
1.使用的是英国的格林威治时间
Instant instant=Instant.now();		//实例化用now方法
System.out.println(instant);		//得到本初子午线时间

2.atOffset设置偏移量
OffsetDateTime atOffset = instant.atOffset(ZoneOffset.ofHours(8));			//东八区时间设置
System.out.println(atOffset);

3.jdk8得到毫秒数用 toEpochMilli方法											//依然是英国的时间
long epochMilli = instant.toEpochMilli();									
System.out.println(epochMilli);

4.毫秒数转化为时间
Instant ofEpochMilli = Instant.ofEpochMilli(epochMilli);
System.out.println(ofEpochMilli);
```

##### 预定义(ISO)<静态>

```
//1.DateTimeFormatter类和LocalDateTime类
DateTimeFormatter dateTimeFormatter=DateTimeFormatter.ISO_LOCAL_TIME;		//预定义格式创建格式化对象
LocalDateTime localTime=LocalDateTime.now();
System.out.println(localTime);

//2.格式化
String format = dateTimeFormatter.format(localTime);
System.out.println(format);

//3.解析
TemporalAccessor parse = dateTimeFormatter.parse(format);
System.out.println(parse);
```

##### 本地创建格式化对象（oflocal）<静态>

##### 自定义创建格式化对象（ofpattern）<静态>

```

```

