## 最近在學的java:
# WEEK_1
### 特性:
- 可以做手機遊戲、中間件、軟體、網站、手機app、伺服器程序、軟體工具、嵌入式領域、大數據技術
- 高安全性、移值性高
### 優勢
- 基礎語法很像C，有程式背景可以馬上學習，但有很多物件的概念。
- 很多職缺需要有能力的java工程師!?
# Java之教案_開工中


## java SE、JAVA EE、JAVAME
- SE(Standard Edition)
    ![](https://i.imgur.com/60JqTvQ.png)

    - EE(Enterprise Edition):以SE為基礎，定義了一系列的服務、API、協定等，適用於開發分散式、多層式（Multi-tier）、以元件為基礎、以Web為基礎的應用程式， 整個Java EE的體系是相當龐大的。
    
    - ME(Micro Edition):小型設備開發與部屬應用程式平台，手機、PDA、股票機
### JVM、JRE、JDK
- ### JVM(JAVA Virtual Machine)
    - ### 具有跨平台功能
        - # 那什麼叫跨平台?
        - 對於電腦而言0、1的序列組成的機器指令。當你使用C/C++時等高階語言會使用編譯器(compiler)，問題在於每個平台認識的0、1序列不同，某個指令會許在windows上也許是0101，但在Linux上可能不同。
        - 所以JAVA編譯時JVM會翻譯成中介<font color="#ff3300">位元碼</font>，而JVM會對應成不同平台的機器碼，且JVM是與底層平台做溝通，可以當作JVM實際就相當於JAVA的作業系統。
        - JAVA 原始碼副檔名 *.JAVA，經過編譯器翻譯為副檔名*.class的位元碼。
    - ### JRE與JDK
        - JRE(JAVA Rountime Environment):JAVA執行環境，包括 JAVA SE API、JAVA JVM
        - JDK(JAVA Development KIT):包括 javac、java、javadoc       

## 進入語法
- 語法
    - ### 基礎語法 與C很像
    - ### print 結果
        - 使用System.out.printf("  ", );//跟C一樣的方式
        - System.out.println()//直接出來變數的值
    - ### 變數
        - final //寫死值 讓變數的值不變
    - ### 運算子與位元運算
        - 加:+
        - 減:-
        - 乘:*
        - 除:/
        - OR:|
        - AND:&&
        - NOT:! 
    - ### 型態轉換
        - float PI=3.14F //用 F告訴編譯器用float型式儲存
    - 流程控制
        - if...else if...else
        - switch_成績分類:
            
            ```java=
            package 基礎語法;

            public class switch_1 {
                public static void main(String[] args) {
                    int score =88;
                    int quotient = score/10;
                    char level;
                    switch(quotient) {
                    case 10:
                    case 9:
                        level='A';
                        break;
                    case 8:
                        level='B';
                        break;
                    case 7:
                        level='C';
                        break;
                    case 6:
                        level='D';
                        break;
                    default:
                        level='E';
                    }
                    System.out.printf("得分等級: %c%n",level);
                }
            }


             ```
             
        - for迴圈_九九乘法表
        ```java=
        package 基礎語法;
            public class for_1 {
                public static void main(String[] args) {
                    for(int i=1;i<10;i++) {
                        for(int j=1;j<10;j++) {
                            System.out.printf("%d*%d=%2d ",i,j,i*j);
                        }
                        System.out.println();
                    }
                }
            }

        ```
        
        - while(條件){ 
           陳述句;
            }
        - do{
            陳述句
            }while(條件);//差異為do先做一次在判斷
        - break
        - continue
## 認識物件
```java=
    package 基礎語法;

class clothes{
	String color;
	char size;
}



public class Field {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		clothes sun =new clothes();
		clothes spring=new clothes();
		
		sun.color="red";
		sun.size='s';
		spring.color="green";
		spring.size='m';
		
		System.out.printf("sun (%s,%c)%n",sun.color,sun.size);
		System.out.printf("spring (%s,%c)%n",spring.color,spring.size);
	}

}
```

### java.util.Scanner
- 功用:接收檔案
- nextInt 看有沒有輸入下一個字串
    
```java=
    package 基礎語法;
    import java.util.Scanner;
    public class java_util_Scanner {
        public static void main(String[] args) {
            // TODO Auto-generated method stub
            Scanner console = new Scanner(System.in);

            int number =(int) (Math.random() *10);
            int guess;
            do {
                System.out.println("猜數字(0~9)");
                guess = console.nextInt();
            }while(guess!= number);
            System.out.println("猜中了~~~!!!!!!");
        }

    }

```

### java.math.BigDecimal // 用來比較值是否相等 而不用==來做判斷
```java=
-package 基礎語法;
import java.math.BigDecimal;

public class BigDecimals {
	public static void main(String[] args) {
		BigDecimal op1=new BigDecimal("0.1");
		BigDecimal op2=new BigDecimal("0.1");
		BigDecimal op3=new BigDecimal("0.1");
		BigDecimal result = new BigDecimal("0.3");
		if(op1.add(op2).add(op3).equals(result)) {
			System.out.println("等於0.3");
		}
		else {
			System.out.println("不等於0.3");
		}
	}
}
``` 

### 物件_比較
```java=
BigDecimal a = new BigDecimal("0.1");
a==>0.1

BigDecimal b = new BigDecimal("0.1");
b==>0.1

BigDecimal c = a;

a==b;
==>false

a==c;
==>true
```
>- why a==b會噴錯，因為這是物件的概念，c綁著a的東西，而b綁著另一個0.1的物件，第五行 c=a; 所以 a跟c都指著同個 0.1所以會true。

### 自動裝箱、拆箱
- 比較時不要用==、!= 要使用equals
- 因為自動裝箱，編譯器會使用Integer.valueOf()建立，IntegerCachelow噢.high 介於-128~127 ，使用JVM指定後，會介於-128~300，So 原本a=100、b=100、a=b會噴是，可是都改成200會噴錯，所以要去更改如上的東西，所以結論就是要使用equals()。
```java=
Integer a=200;
Integer b=200;
if(a.equals(b)){
System.out.println("a=b");
}else{
    System.out.println("a!=b");
}
```

### 陣列&物件
- for 一般寫法與快入寫法
```java=
package 基礎語法;

public class Scores {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int [] scores = {1,2,3,4,5,6,7,8};
//		for(int i=0;i<scores.length;i++) {
//		System.out.printf("學生分數 :%d %n",scores[i]);
//	}
//}
//
		for(int score : scores) {
			System.out.printf("學生分數 :%d %n", score);
		}
	}
}

```
### 2維2*3寫法
```java=
package 基礎語法;

public class array_2維for簡易寫法 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int[] [] arr=new int[2][];
		arr[0]=new int [] {1,2,3,4,5};
		arr[1]=new int [] {1,2,3};
		for(int[] row: arr) {
			for(int value:row){
			System.out.printf("%2d",value);
			}
			System.out.println();
		}
	}
}

```

#### Arrays.fill(陣列名,給予數字):指定陣列初始值
#### Arrays.copyof(要複製陣列名字,陣列名字.length):整個複製陣列值，如果後面*2倍那會後面的值會給0補滿。
### (深層複製)Deepcopy:
```java=
package 基礎語法;



class Clothes2{
	String color;
	char size;
	
	Clothes2(String color,char size){
	this.color=color;
	this.size=size;
	}
}

public class Deep_copy_ex1 {
	public static void main(String[] args) {
	Clothes2[] c1= {new Clothes2("red",'L'),new Clothes2("blue",'M')};
	Clothes2[] c2= new Clothes2[c1.length];//c1有長度給c2
	for(int i=0;i<c1.length;i++) {
		Clothes2 c=new Clothes2(c1[i].color, c1[i].size);
		c2[i]=c;//把值丟給c2
		
		}
		c1[0].color="yello";
		System.out.println(c2[0].color);
	}
}

```
#### length():取得字串長度
#### charAt(數值):去得某個字串的字元
#### toUpperCase():小寫轉大寫
- 寫出sum寫法:
```java=
package 基礎語法;

import java.util.Scanner;

public class String__Sum_1 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner console=new Scanner(System.in);
		long sum=0;
		long number=0;
		do {
			System.out.print("請輸入數字: ");
			number =Long.parseLong(console.nextLine());
			sum+=number;
		}while(number!=0);
		System.out.println("總和: " +sum);
	}

}

```
- 字串特性:相同值時且沒有另設物件時，相同名稱會參考同一物件，而2個變數名稱指著相同東西，但name3、name4是因為"new"另外建立物件。
```java=
String name1="ABC";
String name2="ABC";
String name3=new String("ABC");
String name4=new String("ABC");
System.out.println(name1==name2);==>True
System.out.println(name1==name3);==>False
System.out.println(name3==name4);==>False
```
- 那如果使用System.out.println(name1.equals(name1));時會都是正確，再次強調使用"equals()"的重要而非"=="。


#### 小試身手 ==>1+2+...100
```java=
String text="";
for(int i=0;i<100;i++){
    text=text+i+"+";
}
System.out.println(text+100);

```
## 物件封裝
- private:定義私有，提值時需要提供取值方式,get+上首字大寫單字。
```java=
int getBonus(){
return bonus;
}
```
- 簡化程式
- public:公開類別，表示其他套件可以直接呼叫它。
- this():代表呼叫另一結構式
- static:被宣告的成員不會讓個別擁有，屬於類別，使用Math.定義變數的名稱。
先看以下程式碼===>
![](https://i.imgur.com/oAMaeIS.png)
然後擁有static的PI
![](https://i.imgur.com/1SHmgHp.png)
- import_static_懶人寫法
```java=
package 基礎語法;

import java.util.Scanner;
import static java.lang.System.in;
import static java.lang.System.out;

public class import_static_寫法 {
    public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner console = new Scanner(in);
		out.print("輸入名字");
		out.printf("%s 你好! %n", console.nextLine());
	}
}
```
### Static 超難懂
![](https://i.imgur.com/DRP5LXa.png)
- static 內部不可存取非 static的成員、不可出現this。
- 不定長度引數:解決無法知曉個數。
- 傳值呼叫:注意new 創建新物件 代表程式裡c變數可以指另外新的物件。
```java=
package 基礎語法;
public class 傳值呼叫_01 {
	public static void main(String[] args) {
		Customer c1=new Customer("Justin");
		some(c1);
		System.out.println(c1.name);//John
		
		Customer c2=new Customer("Justin");
		other(c2);
		System.out.println(c2.name);//Justin
	}
	static void some(Customer c) {
		c.name="John";
	}
	static void other(Customer c) {
		c =new Customer("Bill");
	}
}

class Customer {
	String name;
	Customer (String name){
		this.name=name;
	}
}

```
# 繼承與多型
- extends:繼承
```java=
package cc.openhome;

public class Role {
		// TODO Auto-generated method stub
		private String name;
		private int level;
		private int blood;
		
		public int getBlood() {
			return blood;
		}
		public void setBlood(int blood) {
			this.blood = blood;
		}
		
		public int getLevel() {
			return level;
		}
		
		public void setLevel(int level) {
			this.level=level;
		}
		
		public String getName() {
			return name;
		}
		
		public void setName(String name) {
			this.name = name;
		}
		
		
	}

public class SwordMan extends Role{//extends 會擴充Role 的行為與實作，繼承Role行為與實作
	public void fight() {
		System.out.println("揮劍攻擊");
	}
}

public class Magician extends Role{//extends 會擴充Role 的行為與實作，繼承Role行為與實作
	public void fight() {
		System.out.println("魔法攻擊");
	}
	
	public void cure() {
		System.out.println("魔法治療");
	}
}
```
# WEEK_2
## 確定是否有繼承
```java=
package cc.openhome;

public class RPG {
	public static void main(String[] args) {
		demoSwordsMan();
		demoMagician();
	}
	static void demoSwordsMan() {
		SwordMan swordsMan =new SwordMan();
		swordsMan.setName("Justic");
		swordsMan.setLevel(1);
		swordsMan.setBlood(200);
		System.out.printf("劍士 :  (%s, %d, %d)%n",swordsMan.getName(),swordsMan.getLevel(),
				swordsMan.getBlood());
	}
	static void demoMagician() {
		Magician magician =new Magician();
		magician.setName("Monica");
		magician.setLevel(1);
		magician.setBlood(100);
		System.out.printf("魔法師 :  (%s, %d, %d)%n",magician.getName(),magician.getLevel(),
				magician.getBlood());
	}
}
```
## 多型與is-a，翻譯是一種，編譯器的原則，詳請google。
- 繼承增加顯示血量
``` java=
package cc.openhome;

public class RPG {
	public static void main(String[] args) {
		demoSwordsMan();
		demoMagician();
		
		SwordMan swordsMan =new SwordMan();
		swordsMan.setName("Justic");
		swordsMan.setLevel(1);
		swordsMan.setBlood(200);
		
		Magician magician =new Magician();
		magician.setName("Monica");
		magician.setLevel(1);
		magician.setBlood(100);
		
		showBlood(swordsMan);
		showBlood(magician);
	
	}
	static void showBlood(Role role) {
		System.out.printf("%s 血量 %d%n",role.getName(),role.getBlood());
	}
	static void demoSwordsMan() {
		SwordMan swordsMan =new SwordMan();
		swordsMan.setName("Justic");
		swordsMan.setLevel(1);
		swordsMan.setBlood(200);
		System.out.printf("劍士 :  (%s, %d, %d)%n",swordsMan.getName(),swordsMan.getLevel(),
				swordsMan.getBlood());
	}
	static void demoMagician() {
		Magician magician =new Magician();
		magician.setName("Monica");
		magician.setLevel(1);
		magician.setBlood(100);
		System.out.printf("魔法師 :  (%s, %d, %d)%n",magician.getName(),magician.getLevel(),
				magician.getBlood());
	}
}

```

- 重新定義實作(增加Role的攻擊)
```java=
package cc.openhome;

public class RPG {
	public static void main(String[] args) {
		demoSwordsMan();
		demoMagician();
		
		SwordMan swordsMan =new SwordMan();
		swordsMan.setName("Justic");
		swordsMan.setLevel(1);
		swordsMan.setBlood(200);
		
		Magician magician =new Magician();
		magician.setName("Monica");
		magician.setLevel(1);
		magician.setBlood(100);
	
		drawFight(swordsMan);
		drawFight(magician);
	}
	
	static void drawFight(Role role) {
		System.out.print(role.getName());
		role.fight();
    }
}
```
- 抽象方法、抽象類別:abstract
## 繼承語法
- protected
- 呼叫方法使用super，取得父類別中方法定義。

## java.lang.Object
```java=
package cc.openhome;

import java.util.Arrays;

public class ArrayList {
	private Object[] elems;//使用object[]陣列收集
	private int next;//下一個可儲存物件的索引
	
	
	public ArrayList(int capacity){//指定初始容量
		elems=new Object[capacity];
	}
	
	public ArrayList() {
		this(16);	
	}
	
	public void add(Object o) {//收集物件方法
		if(next == elems.length) {//自動增長陣列長度
			elems=Arrays.copyOf(elems,elems.length *2);
		}
		elems[next++]= o;
	}
	public Object get(int index) {//依索引取得收集之物件
		return elems[index];
	}
	public int size() {//已收集物件個數
		return next;
	}
}

```
