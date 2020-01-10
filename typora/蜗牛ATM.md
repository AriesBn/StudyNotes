# 蜗牛ATM四个类

------

#### 1、账户类：

- ###### 属性：账户名称、密码、账户余额

- ###### 方法：带参构造（账户名称、密码）、get/set( 账户名称、密码 )、get( 账户余额 )

  - ###### **set( 账户余额 )-->changeAccountMoney( double  money)**

------

#### 2、账户管理：

- ###### 属性：账户集体、账户集体容量 ( size )、实际账户个数（count）、登陆标记（onlineUserName )

- ###### 方法：无参构造、带参构造（主要目的是为了给集体数组赋size值）、get（size、count、账户集体）

  - ###### register（账户类参）	 <登陆>isAccountExist（账户类参）	<转账名验证> isAccountNameExist（String  toAccountName）

  - ###### deposit（money）  withdraw（money）  transfer（String  toAccountName，money）<双层for>

------

#### 3、界面类（Scanner）

1. ###### registerView（）：输入名称和密码后构造Account	判断用到了while-->continue-->break的格式

2. ###### loginView（）：同样用到了while-->continue-->break的格式、判断密码输入次数在构造Account之后，与“登陆成功”并列

   ```java
       Customer customer = new Customer(registerName, registerPwd);//构造Account
       if(manager.isCustomerExist(customer)){						//判断是否存在账户
           System.out.println("登陆成功");
           break;
       }else{
           count++;												//不存在就计数
           if(count>3){											//大于3就退出系统
               System.out.println("账户冻结");
               System.exit(0);
           }else{
               System.out.println("请重新输入");
               continue;											//账户不存在且输入次数小于3就continue跳出本次循环
           }
       }
   ```

   ###### 3.depositView() 、 withdrawView()、transferView()、showCustomerBalanceView()：这四个方法比较简单

------

#### 4、主菜单类

1. ###### 主方法：new自身调用主菜单

2. ###### 主菜单：用到了while (true){break}的形式      记得switch一定要加break否则会进行到最后一行。

3. ###### 副菜单：用到了while (true){break}的形式