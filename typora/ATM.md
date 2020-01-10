### AccountManger

```java

public class AccountManager {


	  private Account accounts[];//存放很多个账户信息
	  private  int size=5;//最大容量
	  private int count;//实际容量
	  private String loginUser;
	  
	  public AccountManager() {
		// TODO Auto-generated constructor stub
		  
		  accounts=new Account[size];
		  
		  accounts[0]=new Account("admin","123456");
		  accounts[0].changeBlance(100);
		  accounts[1]=new Account("gly","123456");
		  accounts[1].changeBlance(400);
		  count=2;
		  
	  }
	  
	  public AccountManager(int size) {
			// TODO Auto-generated constructor stub
			  this.size=size;
			  accounts=new Account[size];
			  accounts[0]=new Account("admin","123456");
			  accounts[0].changeBlance(100);
			  accounts[1]=new Account("gly","123456");
			  accounts[1].changeBlance(400);
			  count=2;
			  
	  }
		  
	  //增加账户
	  public void addAccount(Account account){
		  accounts[count]=account;
		  count++;
		  
	  }

	  //验证账户对象是否存在
	  public  boolean  isExitAccout(Account account){
		  
		  for (int i = 0; i < count; i++) {
			  
			  if(accounts[i].getAccountName().equals(account.getAccountName())&&accounts[i].getAccountPwd().equals(account.getAccountPwd())){
				  //将登陆成功的用户的用户名存放起来
				  loginUser=account.getAccountName();
				  return true;
				  
			  }
			
		  }
		  
		  return false;
		  
	  }
	  
	  //验证用户名是否存在
	  public boolean isExitAccountName(String accountName){
		  
		  for (int i = 0; i < count; i++) {
			  
			  if(accounts[i].getAccountName().equals(accountName)){
				  //将登陆成功的用户的用户名存放起来
				  
				  return true;
				  
			  }
			
		  }
		  
		  return false;
		  
	  }
	  
	  //转账
	  public  void transfer(String otherAccountName,double  vb){
		  
		  //遍历找到两个账户
		  for (int i = 0; i < count; i++) {
			  //找登录的账户
			  if(accounts[i].getAccountName().equals(loginUser)){
				  
				  accounts[i].changeBlance(-vb);
			  }
			  //找另外一个账户
			  if(accounts[i].getAccountName().equals(otherAccountName)){
				  
				  accounts[i].changeBlance(vb);
			  }
		  }
	  }
	  
	  public double getLoginUserBalance(){
		  
		
			  
			 
			  for (int i = 0; i < count; i++) {
				  //找登录的账户
				  if(accounts[i].getAccountName().equals(loginUser)){
					  
					  return accounts[i].getAccountBlance();
				  }
				
			  }
			  
			  return 0;
		  
	  }
	  
	  
	  //存钱
	  public  void transfer(double  vb){
		  
		  //遍历找到两个账户
		  for (int i = 0; i < count; i++) {
			  //找登录的账户
			  if(accounts[i].getAccountName().equals(loginUser)){
				  
				  accounts[i].changeBlance(vb);
			  }
			
			  
		  }
	  }
	  
	  
	 //取钱
	  
	  
	  //测试过程中，获得所有的账户
	  public Account[] getAccounts() {
		return accounts;
	 }
	  
	  public int getCount() {
		return count;
	}
	  
	  public int getSize() {
		return size;
	}
	  
}

```

### ManagerView

```java
import java.util.Scanner;

public class AccountView {

	private AccountManager am=new AccountManager();
	
	public void registerView(){
		Scanner sc=new Scanner(System.in);
		while(true){
			System.out.println("请输入用户名");
			String accountName=sc.next();
			if(am.isExitAccountName(accountName)){
				
				System.out.println("您输入的用户名已经存在，请重新输入");
				continue;
				
			}
			
			System.out.println("请输入密码");
			String accountPwd=sc.next();
			System.out.println("请确认密码");
			String accountPwd1=sc.next();
			
			if(!accountPwd.equals(accountPwd1)){
				
				System.out.println("请重新输入");
				continue;
			}
			//将用户名和密码封装为账户对象
			Account account=new Account(accountName,accountPwd);
			am.addAccount(account);
			System.out.println("注册成功");
			break;
		}
	}
	
	public void loginView(){
		
		Scanner sc=new Scanner(System.in);
		int count=0;
		while(true){
			System.out.println("请输入用户名");
			String accountName=sc.next();
			System.out.println("请输入密码");
			String accountPwd=sc.next();
			
			Account account=new Account(accountName, accountPwd);
			
			if(am.isExitAccout(account)){
				
				System.out.println("登录成功");
				break;
			}
			else{
				//限制密码错误的次数
				count++;
				if(count>3){
					System.out.println("您的账户已经冻结。。。。，系统即将退出");
					System.exit(0);//退出系统
				}
				else{
					System.out.println("n您输入的用户名或者密码不正确，请重新输入");
					continue;
				}
			}
		}
		
	}
	
	
	
	public  void transferView(){
		Scanner sc=new Scanner(System.in);
		String ans="y";
		while(ans.equals("y")){
			System.out.println("请输入对方账户");
			String accountName=sc.next();
			if(!am.isExitAccountName(accountName)){
				System.out.println("您输入的账户不存在，请重新输入");
				continue;
			}
			
			System.out.println("请输入转账金额");
			double money=sc.nextDouble();
			
			am.transfer(accountName, money);
			
			System.out.println("是否要继续转账");
			ans=sc.next();
		}
	}
	
	//展示自己账户的余额
	public  void showMoney(){
		
		
		double money=am.getLoginUserBalance();
		System.out.println("您的账户余额为:"+money);
	}
	
	
	//测试，展示所有账户信息
	
	public void showAll(){
		Account accounts[]=am.getAccounts();
		for (int i = 0; i < am.getCount(); i++) {
			System.out.println(accounts[i]);
		}
		
		
	}
	
	//存钱界面，自己完成

}

```

### MainMenu

```java
import java.util.Scanner;

public class Main {
	
	private AccountView  accountView=new AccountView();
	public void mainMenu(){
		Scanner sc=new Scanner(System.in);
		
		while(true){
			System.out.println("1.注册");
			System.out.println("2.登录");
			System.out.println("请选择");
			int se=sc.nextInt();
			
			switch (se) {
			case 1:
				accountView.registerView();
				
				break;
			case 2:
				accountView.loginView();
				subMenu();
				break;
	
			default:
				break;
			}
		}
		
	}
	
	
	public void subMenu(){
		
		Scanner sc=new Scanner(System.in);
		
		while(true){
			System.out.println("1.转账");
			System.out.println("2.查询余额");
			System.out.println("3.存钱");
			System.out.println("4.取钱");
			System.out.println("5.展示所有账户");
			System.out.println("6.返回十一级");
			System.out.println("请选择");
			int se=sc.nextInt();
			
			switch (se) {
			case 1:
				accountView.transferView();
				break;
			case 2:
				accountView.showMoney();
				break;
			case 3:
				//启动存钱界面
				break;
			case 4:
				//启动取钱界面
				break;
			case 5:
				accountView.showAll();
				break;
			default:
				mainMenu();
				break;
			}
		}
	}
	
	public static void main(String[] args) {
		
		Main m=new Main();
		m.mainMenu();//启动主菜单
		
	}

}

```

