---
coverY: 0
---

# 刷题记录

## 首字母缩略词

**题目描述**

```
有一种简单的的加密方法，对给定的一个字符串，把其中从a-y，A-Y的字母用其后继字母替代，把z和Z用a和A替代，其余非字母的字符不变，则可得到一个简单的加密字符串
```

**输入**

```
输入一行字符串（可能包含空格），长度小于80个字符。
输出加密后的字符串
```

**代码**

```c
#include <stdio.h>
#include <string.h>
//#include <ctype.h>
int main(){
    char s[100000];
    int i=0,j;
    gets(s);
    for(int i=0;i<strlen(s);i++){
    if((s[i]>='a'&&s[i]<='z')||(s[i]>='A'&&s[i]<='Z')){
        if(s[i]=='z'||s[i]=='Z')s[i]-=26;
        putchar(s[i]+1);
    }
    else
        putchar(s[i]);
    }
    
    return 0;
}
```

## 字符串排序

**题目描述**

```
输入一组字符串，不超过100个，将输入的字符串按照升序排列并输出（每行一个）
```

**输入**

```
每行输入一个字符串（即：每个字符串以换行符号作为结束）每个字符串长度不超过25 
读取直到输入结束
```

**代码**

```c
#include <stdio.h>
#include <string.h>
int main()
{
	int n=0,i=0;
	char a[100][100];

	while(scanf("%s",&a[i])!=EOF)i++;

	for(int j=0;j<i-1;j++){
		for(int k=0;k<i-j-1;k++){
			if(strcmp(a[k],a[k+1])>0){
				char t[100];
				strcpy(t,a[k]);
				strcpy(a[k],a[k+1]);
				strcpy(a[k+1],t);
			}
		}
	}
	
	for(int j=0;j<i;j++)
		printf("%s",a[j]);
	return 0;
}
```

## 杨辉三角

**题目描述**

```
输入非负整数N（0≤N≤30），输出杨辉三角。 
为了简化问题，不同行之间的数值不需要对齐，只要求每一行内两个数值之间的间隔为有一个空格。
```

**输入**

```
4
```

**输出**

```
1
1 1
1 2 1
1 3 3 1
1 4 6 4 1
```

**代码**

```c
#include<stdio.h>
#include<string.h>
int main()
{
    int a[100][100]={0};
    int x=0,y=0,n;
    scanf("%d",&n);
    a[1][1]=1;
    for(x=1;x<=n+1;x++)
        for(y=0;y<=x;y++)
            a[x+1][y+1]=a[x][y]+a[x][y+1];
    for(x=1;x<=n+1;x++){
        for(y=1;y<=x;y++){
            printf("%d ",a[x][y]);
        }printf("\n");
    }
       
    return 0;
}
```

## 奇数阶幻方

**题目描述**

![](http://wlacm.com/upload/image/20180419/20180419124318\_22800.jpg#id=vdaBp\&originHeight=194\&originWidth=194\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

```
幻方（Magic Square）是一种中国传统游戏，游戏要求将1～N2的数值安排在正方形格子中，使每行、列和对角线上的相加之和都相等 
   幻方的解法有很多种，当N为奇数时有1种构造方法，叫做“右上方连续摆数” ，按照这种方法，当N=3，5，7时，幻方的布局为 
3 
8 1 6 
3 5 7 
4 9 2 
5 
17 24 1 8 15 
23 5 7 14 16 
 4 6 13 20 22 
10 12 19 21 3 
11 18 25 2 9 
7 
30 39 48 1 10 19 28 
38 47 7 9 18 27 29 
46 6 8 17 26 35 37 
 5 14 16 25 34 36 45 
13 15 24 33 42 44 4 
21 23 32 41 43 3 12 
22 31 40 49 2 11 20 
第1行中间的数总是1，最后1行中间的数是N2，N2的右边是2，从这三个幻方，可看出“右上方”具有出界回绕的含义。有人将这个规律总结为：奇幻七绝 
先填上行正中央， 
依次斜填切莫忘。 
上格没有顶格填， 
顶格没有底格放。
```

**输入**

```
正整数N（N≤19）
```

**输出**

```
奇数阶幻方，幻方中的每个数值占4格，右对齐，每行以\n结尾。输出格式详见样例
```

```c
#include<stdio.h>
#include<string.h>
int main()
{
    int n;
    int f[20][20];
    scanf("%d",&n);
    int k=1,y=n,x=(n+1)/2;
    while(k<=n*n){
        if(x==0)
        x=n;
        if(y==n+1)
        y=1;
        f[x--][y++]=k++;
        if((k-1)%n==0){
            x++;
            y-=2;
        }
    }
    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            printf("%4d",f[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```

## 字符串简单加密

**题目描述**

```
有一种简单的的加密方法，对给定的一个字符串，把其中从a-y，A-Y的字母用其后继字母替代，把z和Z用a和A替代，其余非字母的字符不变，则可得到一个简单的加密字符串
```

**输入**

```
输入一行字符串（可能包含空格），长度小于80个字符
```

**输出**

```
输出加密后的字符串
```

```c
#include <stdio.h>
#include <string.h>
//#include <ctype.h>
int main(){
    char s[100000];
    int i=0,j;
    gets(s);
    for(int i=0;i<strlen(s);i++){
    if((s[i]>='a'&&s[i]<='z')||(s[i]>='A'&&s[i]<='Z')){
        if(s[i]=='z'||s[i]=='Z')s[i]-=26;
        putchar(s[i]+1);
    }
    else
        putchar(s[i]);
    }
    
    return 0;
}
```

## **交换最小值和最大值**

**题目描述**

```
本题要求编写程序，先将输入的一系列整数中的最小值与第一个数交换，然后将最大值与最后一个数交换，最后输出交换后的序列。
注意：题目保证最大和最小值都是唯一的
```

**输入**

```
输入在第一行中给出一个正整数N（≤10），第二行给出N个整数，数字间以空格分隔
```

**输出**

```
在一行中顺序输出交换后的序列，每个整数后跟一个空格
```

**输入样例：**

```properties
5
8 2 5 1 4
```

**输出样例：**

```
1 2 5 4 8
```

```c
#include<stdio.h>

int main()
{
	int n,a[10000],min=0,max=0,ma=0,mi=0,t=0;
	scanf("%d",&n);
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);

    min=a[0];						//存入最小值min
    for(int i=1;i<n;i++){
        if(a[i]<min){
            mi=i;
            min=a[i];
        }
    }
    t=a[0];							//第一位和min交换
    a[0]=a[mi];
    a[mi]=t;

    max=a[0];						//存入最大值m
    for(int i=1;i<n;i++){
        if(a[i]>max){
            ma=i;
            max=a[i];
        }
    }
    t=a[n-1];						//最后一位和max交换
    a[n-1]=a[ma];
    a[ma]=t;
    
    for(int i=0;i<n;i++)
        printf("%d ",a[i]);
	return 0;
}
```

## **求一批整数中出现最多的个位数字**

```
给定一批整数，分析每个整数的每一位数字，求出现次数最多的个位数字。例如给定3个整数1234、2345、3456，其中出现最多次数的数字是3和4，均出现了3次
```

**输入格式：**

```
输入在第1行中给出正整数N（≤1000），在第二行中给出N个不超过整型范围的非负整数，数字间以空格分隔
```

**输出格式：**

```
在一行中按格式“M: n1 n2 ...”输出，其中M是最大次数，n1、n2、……为出现次数最多的个位数字，按从小到大的顺序排列。数字间以空格分隔，但末尾不得有多余空格
```

**输入样例：**

```properties
3
1234 2345 3456
```

**输出样例：**

```
3: 3 4
```

**题解：**

```c
#include<stdio.h>
#include<math.h>
int main()
{
	int n,num,a[100],t,b[1000]={0},number;
	scanf("%d",&n);
	for(int i=0;i<n;i++){
		scanf("%d",&number);
            while(number){
            b[number%10]++;
            number/=10;
        }
    }
    
    /*for(int i=0;i<10;i++)
        printf("%d ",b[i]);
    printf("\n");*/
    //b[1000]存储出现数字的次数，eg.b[2]中2出现的次数，b[3]中3出现的次数

    int max=b[0];
    for(int i=1;i<10;i++){
        if(max<b[i])
            max=b[i];
    }

    printf("%d:",max);

    for(int i=0;i<10;i++){
        if(max==b[i]){
            printf(" %d",i);
        }
    }
            
        
	return 0;
}
```

## 【函数】判断正整数N（N>1）是否为素数

**题目描述**

```c
对于正整数N（1<N<10000），如果N只能被1和N整除，则N为素数，否则N为合数
请写一个函数实现。函数声明如下：

//判断一个数是否为素数
int isPrime(int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
int main()
{
	int m;
    while(scanf("%d",&m)!=EOF){
            if(isPrime(m))
                printf("prime\n");
            else
                printf("composite\n");
    }
	return 0;
}
```

**输入**

```
输入一个正整数N（1<N<10000)。测试数据有多组，处理到输入结束
```

**输出**

```
如果是素数，则输出"prime"，否则输出“composite”
每个输出占1行
```

**样例输入**

```
2
3
4
```

**样例输出**

```
prime
prime
composite
```

**题解：**

```c
int isPrime(int n){
    int k=sqrt(n*1.0);
    if(n==2)return 1;
    for(int i=2;i<=k;i++)
        if(!(n%i))return 0;
    return 1;
}
```

## 【函数】自定义函数：利用辗转相除法求最大公约数

**题目描述**

```
本题要求实现一个自定义函数：利用辗转相除法求最大公约数。
函数接口定义：

int gcd(int a, int b);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
int gcd(int a,int b);
int main()
{
	int a,b;
    while(scanf("%d%d",&a,&b)!=EOF)
        printf("%d\n",gcd(a,b));
}
```

辗转相除法，是目前已知最古老的算法, 可追溯至公元前300年。

它首次出现于欧几里德（Euclidean）的《几何原本》（第VII卷，命题i和ii）中，在中国可以追溯至东汉时期的《九章算术》

辗转相除法计算两个正整数a和b的最大公约数，步骤描述如下：

* (1) 如果b为0则最大公约数为a，算法结束
* (2) 令r为a÷b所得余数
* (3) 令a←b，b←r，并返回步骤(1)

**输入**

```
输入正整数a,b；
测试数据有多组，处理到输入结束。
```

**输出**

```
输出a和b的最大公约数，每个输出占1行。
```

**样例输入**

```
24 60
18 15
23 21
```

**样例输出**

```
12
3
1
```

**题解：**

```c
int gcd(int a,int b)
{
    if(a<b){
        int t=a;
        a=b;
        b=t;
    }
    if(a%b==0) return b;
    else gcd(b,a%b);
}
```

## 【函数】自定义函数：正整数第K位的数字

**题目描述**

```c
本题要求实现一个自定义函数：返回值为正整数n的第k位的数字（从右向左数）。
函数接口定义：

int getK(int n, int k);

其中n和k是用户传入的参数，如果k≤n，则该函数必须返回第k位数字，否则返回0
```

**输入**

```
正整数n,k
测试数据有多组，处理到输入结束
```

**输出**

```
n的第k位数字，每个输出占1行
```

**样例输入**

```
54321 1
54321 8
987654321 7
```

**样例输出**

```
1
0
7
```

**裁判测试程序样例：**

```
#include<stdio.h>
int getK(int n, int k);
int main(){
    int n,k;
    while(scanf("%d%d",&n,&k)!=EOF)
        printf("%d\n",getK(n,k));
        return 0;
}
```

**题解：**

```c
int getK(int n, int k){
    int i=1;
    while(n){
        if(i==k)return n%10;
        n/=10;
        i++;
    }
    return 0;
}
```

## 【函数】十进制转二进制

**题目描述**

```c
输入一个十进制数N（32位整数），将它转换成二进制数输出。 要求用函数实现，并提交该函数定义。 
本题要求实现1个自定义函数：将十进制转换成二进制并输出。
函数接口定义：

//输入一个十进制数，转换为2进制并输出    

void  decToBin(int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
void decToBin(int);
int main(){
    int x;
    while(scanf("%d",&x)!=EOF)
        decTobin(x);
        return 0;
}
```

**输入**

```
输入数据包含多个测试实例，每个测试实例包含1个整数N(32位整数)
```

**输出**

```
输出转换后的数，每个输出占1行
```

**样例输入**

```
55 
-23
42
-2
```

**样例输出**

```
110111
-10111
101010
-10
```

**题解：**

```c
void  decToBin(int n){
    int i=0;
    int a[1000];
    if(!n)
        printf("0");
    if(n<0){
        printf("-");
        n=-n;
    }
    while(n){
        a[i++]=n%2;
        n/=2;
    }
    for(i-=1;i>=0;i--)
        printf("%d",a[i]);
}
```

## 【函数】十进制转成R进制

**题目描述**

```
输入一个十进制数N(32位整数)，将它转换成R（2<=R<=16）进制数输出。
要求用函数实现。
本题要求实现1个自定义函数：将十进制转换成R进制并输出
```

**函数接口定义：**

```
//输入一个十进制数，转换为R进制并输出 
void  decToR(int,int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
void decToR(int ,int );
int main(){
    int x,r;
    while(scanf("%d%d",&x,&r)!=EOF){
        int i,n;
        decToR(x,r);
        printf("\n");
    }
}
```

**输入**

```
输入数据包含多个测试实例，每个测试实例包含两个整数N(32位整数)和R（2<=R<=16）
```

**输出**

```
输出转换后的数。如果R大于10，则对应的数字规则参考16进制（比如，10用A表示，等等）
```

**样例输入**

```
23 12
-4 3
```

**样例输出**

```
1B
-11
```

**题解：**

```c
void decToR(int n,int r){
    char str[40]="0123456789ABCDEF";
    int i=0;
    char c[1000];
    int a[1000];
    if(!n)
        printf("0");
    if(n<0){
        printf("-");
        n=-n;
    }
    while(n){
        c[i++]=str[n%r];
        n/=r;
    }
    for(i-=1;i>=0;i--)
        printf("%c",c[i]);
}
```

## 【函数】组合数函数及阶乘函数

**题目描述**

```
利用阶乘函数计算组合数
```

![](http://wlacm.com/upload/pimg1041\_1.png#id=Y22DO\&originHeight=158\&originWidth=435\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

```
本题要求实现2个自定义函数：求组合数函数和求阶乘函数。
```

**函数接口定义：**

```c
int comb(int m,int n);

int fac(int x);
```

**裁判测试程序样例：**

```c
#include<stdio.h>

int fac(int x);
int main(void);
int main(){
    int a,b;
    while(scanf("%d%d",&a,&b)!=EOF)
        printf("%d\n",comb(a,b));
}
```

**输入**

```
测试数据有多组，处理到输入结束。
```

**输出**

```
每行一个输出结果。
```

**样例输入**

```
6 3
5 1
```

**样例输出**

```
20
5
```

**题解：**

```c
int comb(int m,int n){
    return fac(m)/(fac(n)*fac(m-n));
}

int fac(int x){
    int i,s = 1;
    for(i=1;i<=x;i++)
        s*=i;
    return s;
}
```

## **输出前 n 个Fibonacci数**

```
本题要求编写程序，输出菲波那契（Fibonacci）数列的前N项，每行输出5个，题目保证输出结果在长整型范围内。Fibonacci数列就是满足任一项数字是前两项的和（最开始两项均定义为1）的数列，例如：1，1，2，3，5，8，13，...
```

**输入格式**:

```
输入在一行中给出一个整数N（1≤N≤46）
```

**输出格式:**

```
输出前N个Fibonacci数，每个数占11位，每行输出5个。如果最后一行输出的个数不到5个，也需要换行
如果N小于1，则输出"Invalid."
```

**输入样例**1:

```properties
7
```

**输出样例**1:

```
          1          1          2          3          5
          8         13
```

**输入样例**2：

```
0
```

**输出样例**2：

```
Invalid.
```

**题解：**

```c
#include<stdio.h>

int main()
{
	int n,t=0;
    scanf("%d",&n);
    if(n<1){
        printf("Invalid.");
        return 0;
    }
    int a[100]={0};
    a[1]=1;
    for(int i=1;i<=n;i++){
        a[i+2]=a[i]+a[i+1];
        printf("%11d",a[i+2]);
        t++;
        if(t%5==0)
            printf("\n");
    }
}
```

## **输出m到n之间的全部素数**

```
本题要求输出给定整数M和N区间内的全部素数，每行输出10个。素数就是只能被1和自身整除的正整数。注意：1不是素数，2是素数。
```

**输入格式**:

```
输入在一行中给出两个正整数*M*和*N*（1≤*M*≤*N*≤500）。
```

**输出格式**:

```
输出素数，每个数占6位，每行输出10个。如果最后一行输出的素数个数不到10个，也需要换行
若输入的范围不合法，则输出"Invalid."
```

**输入样例1:**

```properties
2 100
```

**输出样例1:**

```
     2     3     5     7    11    13    17    19    23    29
    31    37    41    43    47    53    59    61    67    71
    73    79    83    89    97
```

**输入样例2:**

```properties
6 2
```

**输出样例2:**

```
Invalid.
```

\*\*题解：\*\*错误的

```c
#include<stdio.h>
#include<math.h>
int main(){
    int m,n,i,j,count=0,num=0;
    scanf("%d%d",&m,&n);
    if(m<1||n>500||m>n){
        printf("Invaild.");
        return 0;
    }
    if(m==1)m++;
    
    for(i=2;i<=n;i++){//i是m到n
        int t=0;
        for(j=2;j<=sqrt(i*1.0);j++)//j是1到m
            if(i%j==0)
                t=1;

        if(!t){
            printf("%6d",i);
            count++;
            
            if(count%10==0)
                printf("\n");
            
        }
    }
        //printf("\ncount=%d",count);
    if(count%10==0)
        return 0;
    else
        if(count%10<10)
            printf("\n");
    return 0;
}
```

```c
//正确的
#include<stdio.h> 
#include<math.h>
int main()
{
	int count,i,k,flag,limit,m,n;
    scanf("%d%d", &m,&n);
    count=0;
    if(m<1||n>500||m>n){
        printf("Invalid.\n");
    }else{
        for(k=m;k<=n;k++){
            if(k<=1){
                flag=0;
            }else if(k==2){
                flag=1;
            }else{
                flag=1;
                limit=sqrt(k)+1;
                for(i=2;i<=limit;i++){
                    if(k%i==0){
                        flag=0;
                        break;
                    }
                }
            }
            if(flag==1){
                printf("%6d", k);
                count++;
                if(count%10==0){
                    printf("\n");
                }
            }
        }
    }
	return 0;
}
```

## **穷举问题-搬砖**

```
某工地需要搬运砖块，已知男人一人搬3块，女人一人搬2块，小孩两人搬1块。如果想用n人正好搬n块砖，问有多少种搬法？
```

**输入格式:**

```
输入在一行中给出一个正整数n。
```

**输出格式:**

```
输出在每一行显示一种方案，按照"`men = cnt_m, women = cnt_w, child = cnt_c`"的格式，输出男人的数量cnt_m，女人的数量cnt_w，小孩的数量cnt_c。请注意，等号的两侧各有一个空格，逗号的后面也有一个空格。
如果找不到符合条件的方案，则输出"None"
```

**输入样例：**

```properties
45
```

**输出样例:**

```
men = 0, women = 15, child = 30
men = 3, women = 10, child = 32
men = 6, women = 5, child = 34
men = 9, women = 0, child = 36
```

**题解：**

```c
#include<stdio.h>
int main()
{
	int n,a,b,c,count=0;
	scanf("%d",&n);
    for(a=0;a<=n;a++){
	    for(b=0;b<=n;b++){
	        for(c=0;c<=n;c++){
		        if(a+b+c==n&&3*a+2*b+c*0.5==n){ //注意计算a,b,c的条件
		    	    printf("men = %d, women = %d, child = %d\n",a,b,c);
		    	    count++;
			    } 
            }	
		}
	}	
	if(count==0) printf("None"); //用count来表示方案个数
	return 0;
}
```

## 【递归】求阶乘

```
利用递归函数求阶乘
本题要求实现1个自定义函数：求阶乘函数
函数接口定义：
```

```
long long fac(int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>

long long fac(int);
int main(){
    int n;
    while(scanf("%d",&n)!=EOF)
        printf("%lld\n",fac(n));
    
}
```

**输入**

```
输入正整数n(n<=20)
测试数据有多组，处理到输入结束
```

**输出**

```
每行一个输出结果
```

**样例输入**

```
1
2
3
4
5
```

**样例输出**

```
1
2
6
24
120
```

**题解：**

```c
long long fac(int x){
    long long i,s = 1;
    for(i=1;i<=x;i++)
        s*=i;
    return s;
}
```

## 【递归】用递归求x的n次方

```
本题要求实现1个自定义函数：求x的n次方（已知x为实数，n为自然数）
```

**函数接口定义：**

```c
double mypow(double,int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
#include<math.h>
double mypow(double,int);
int main(){
    int n;
    double x;
    while(scanf("%lf%d",&x,&n)!=EOF)
        printf("%.3lf\n",mypow(x,n));
    
}
```

**输入**

```
从键盘，输入x，n，测试数据有多组，处理到文件结尾
```

**输出**

```
输出x的n次方，结果保留3位小数
```

**样例输入**

```
10 2
3 4
5.2 1
```

**样例输出**

```
100.000
81.000
5.200
```

**题解：**

```c
double mypow(double s,int r){
    return pow(s,r);
}
```

## 【递归】输出m和n之间的所有整数

```
本题要求实现一个递归函数：按照从小到大顺序输出m和n之间的所有整数(包括m和n)
```

**函数接口定义：**

```c
void print(int m,int n);
```

**裁判测试程序样例：**

```c
#include<stdio.h>

void print(int m,int n);
int main(){
    int m,n;
    while(scanf("%d%d",&m,&n)!=EOF)
        print(m,n);
        printf("\n");
    return 0;
}
```

**输入**

```
输入整数m和n(-10<=m<=10,-10<=n<=10)；
测试数据有多组，处理到输入结束。
```

**输出**

```
按照从小到大顺序输出m和n之间的所有整数（包括m和n），2个整数之间用空格隔开;
每个输出占 1行。
```

**样例输入**

```
3 -3
-2 1
4 4
```

**样例输出**

```
-3 -2 -1 0 1 2 3
-2 -1 0 1
4
```

**题解：**

```c
void print(int m,int n){
    if(m>n){
        int t=m;
        m=n;
        n=t;
    }
    for(int i=m;i<=n;i++){
        printf("%d ",i);
    }
}
```

## 【递归】求组合数

![](http://wlacm.com/upload/pimg1333\_1.png#id=hNnoj\&originHeight=228\&originWidth=1273\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

**题目描述**

```
本题要求实现1个自定义函数：求组合数函数。
```

**函数接口定义：**

```c
int comb(int m,int n);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
#include<math.h>
int comb(int m,int n);
int main(){
    int a,b;
    while(scanf("%d%d",&a,&b)!=EOF)
        printf("%d\n",comb(a,b));
    return 0;
}
```

**输入**

```
测试数据有多组，处理到输入结束
```

**输出**

```
每行一个输出结果
```

**样例输入**

```
6 3
5 1
```

**样例输出**

```
20
5
```

**提示:**

![](http://wlacm.com/upload/image/20180523/20180523213859\_64761.png#id=CDijz\&originHeight=388\&originWidth=950\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

**题解：**

```c
int comb(int m,int n){
  if(n==m||n==0)
      return 1;
  if(n>m/2)
      n=m-n;
  return comb(m-1,n)+comb(m-1,n-1);
}
```

## 【递归】利用辗转相除法求最大公约数

```
本题要求实现一个递归函数：利用辗转相除法求最大公约数
```

**函数接口定义：**

```c
int gcd(int a, int b);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
int gcd(int a,int b);
int main()
{
	int a,b;
    while(scanf("%d%d",&a,&b)!=EOF)
        printf("%d\n",gcd(a,b));
}
```

```
辗转相除法，是目前已知最古老的算法, 可追溯至公元前300年。 
它首次出现于欧几里德（Euclidean）的《几何原本》（第VII卷，命题i和ii）中，在中国可以追溯至东汉时期的《九章算术》 
辗转相除法计算两个正整数a和b的最大公约数，步骤描述如下： 
(1) 如果b为0则最大公约数为a，算法结束 
(2) 令r为a÷b所得余数 
(3) 令a←b，b←r，并返回步骤(1)
```

**输入**

```
输入正整数a,b；
测试数据有多组，处理到输入结束。
```

**输出**

```
输出a和b的最大公约数，每个输出占1行
```

**样例输入**

```
24 60
18 15
23 21
```

**样例输出**

```
12
3
1
```

**题解：**

```c
int gcd(int a, int b){
  int r;
  if(!b)return a;
  if(!a)return b;
  return gcd(b,a%b);
}
```

## 走楼梯

**题目描述**

```
楼梯有n级台阶，上楼可以一步上一阶，也可以一步上二阶。编一程序，计算共有多少种不同走法？
本题要求用递归算法实现
```

**输入**

```
输入n(n<=50)
```

**输出**

```
输出走法的总数
```

**样例输入**

```
3
```

**样例输出**

```
3
```

**题解：**

```c
#include <stdio.h>

int fun(int n)
{
    if (n>0)
    {
        if (1 == n)
        {
            return 1;
        }
        else if (2 == n)
        {
            return 2;
        }
        else
        {
            return fun(n-1) +fun(n-2);
        }
    }
    else
        return 0;
}

int main()
{
    int n;
    scanf("%d",&n);
    printf("%d",fun(n));
    return 0;
}
```

## 【递归】汉诺塔（Haono）问题

**题目描述**

```
	汉诺塔（又称河内塔）问题是印度的一个古老的传说。开天辟地的神勃拉玛在一个庙里留下了三根金刚石的柱子A、B和C，A上面套着n个圆的金片， 最大的一个在底下，其余一个比一个小，依次叠上去， 庙里的众僧不倦地把它们一个个地从A柱搬到C柱上，规定可利用中间的一根B柱作为帮助， 但每次只能搬一个， 而且大的不能放在小的上面。 僧侣们搬得汗流满面，可惜当n很大时这辈子恐怕就搬不完了。 
	聪明的你还有计算机帮你完成，你能写一个程序帮助僧侣们完成这辈子的夙愿吗？ 
	本题要求实现1个自定义函数，输出搬动金片的全过程。
```

**函数接口定义：**

```c
//将n个圆盘从A柱移到C柱上去（借助B柱） 
void move(int n,char a,char b,char c)
```

**裁判测试程序样例：**

```c
#include<stdio.h>
#include<math.h>
void move(int n,char a,char b,char c):
int main(){
    int n;
    while(scanf("%d",&n!=EOF)){
        move(n,'A','B','C');
        printf("\n");
    }
    return 0;
}
```

**输入**

```
输入金片的个数n（n>=1并且n<=10)，测试数据有多组，处理到文件结尾
```

**输出**

```
输出搬动金片的全过程。每组输出结果后，都空一行，格式见样例输出
```

**样例输入**

```
2
3
```

**样例输出**

```
move 1# from A to B
move 2# from A to C
move 1# from B to C

move 1# from A to C
move 2# from A to B
move 1# from C to B
move 3# from A to C
move 1# from B to A
move 2# from B to C
move 1# from A to C
```

**题解：**

## 【递归】十进制转二进制

**题目描述**

```
输入一个十进制数N（32位整数），将它转换成二进制数输出
```

**函数接口定义：**

```c
//输入一个十进制数，转换为2进制并输出 
void  decToBin(int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
#include<math.h>
void  decToBin(int);
int main(){
    int x;
    while(scanf("%d",&x)!=EOF){
        decToBin(x);
        printf("\n");
    }
    return 0;
}
```

**输入**

```
输入数据包含多个测试实例，每个测试实例包含1个整数N(32位整数)
```

**输出**

```
输出转换后的数，每个输出占1行
```

**样例输入**

```
55 
-23
42
-2
```

**样例输出**

```
110111
-10111
101010
-10
```

**题解：**

```c
void  decToBin(int n){
    if(n<0){
        printf("-");
        n=-n;
    }
    if(n/2>0)
      decToBin(n/2);
    
    printf("%d",n%2);
    
}
```

## 【递归】十进制转成R进制

**题目描述**

```
输入一个十进制数N(32位整数)，用递归算法将它转换成R（2<=R<=16）进制数输出。
```

**函数接口定义：**

```c
//输入一个十进制数，转换为R进制并输出 
void  decToR(int,int);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
void decToR(int ,int );
int main(){
    int x,r;
    while(scanf("%d%d",&x,&r)!=EOF){
        int i,n;
        decToR(x,r);
        printf("\n");
    }
}
```

**输入**

```
输入数据包含多个测试实例，每个测试实例包含两个整数N(32位整数)和R（2<=R<=16）。
```

**输出**

```
输出转换后的数。如果R大于10，则对应的数字规则参考16进制（比如，10用A表示，等等）
```

**样例输入**

```
23 12
-4 3
```

**样例输出**

```
1B
-11
```

**题解：**

```c
void decToR(int n,int m){
    char str[40]="0123456789ABCDEF";
    char a[1000],i=0;
    if(n<0){
        printf("-");
        n=-n;
    }
    if(n/m>0)
      decToR(n/m,m);
      
    printf("%c",str[n%m]);
}
```

## 【递归】分梨

**题目描述**

```
阿布喜欢吃梨，有一天妈妈买了一筐梨子。小伙伴们来做客，他想和小伙伴们一起分享。现在他要把m个梨放到n个盘子里面 （我们允许有的盘子为空），你能告诉阿布有多少种分法吗？（请注意，如果有三个盘子，我们将5,1,1和1,1,5，视为同一种分法）
```

**函数接口定义：**

```c
//用递归算法求m个梨放在n个盘子里的方法总数 
int f(int m,int n);
```

**裁判测试程序样例：**

```c
#include<stdio.h>
#include<math.h>
int f(int m,int n);  
int main(){
    int n;
    while(n--){
        int a,b;
        scanf("%d%d",&a,&b);
        printf("%d\n",f(a,b));
    }
    return 0;
}
```

**输入**

```
第一行是一个整数t，代表有t组样例
第二行有两个整数M和N代表有M个梨和N个盘子
```

**输出**

```
输出有多少种方法
```

**样例输入**

```
1
7 3
```

**样例输出**

```
8
```

**提示**

```
m个梨放在n个盘子，允许有盘子空，按层次可以划分成如下的子问题 
1) 在n个盘子中不空的放。显然此时方法种数相当于在n个盘子里面放（m - n）个苹果 
2) n个盘子中至少有一个空，即盘子规模小1的子问题。
```

**题解：**

```c
int f(int m,int n)  
{         
  if(n==1||m==0)  
    return 1;  
  if(m<n)        
    return f(m,m);  
  else  
    return f(m,n-1)+f(m-n,n);                 
}
```

## 使用函数计算两点间的距离

```
本题要求实现一个函数，对给定平面任意两点坐标(x1,y1)和(x2,y2)，求这两点之间的距离
```

**函数接口定义：**

```c
double dist( double x1, double y1, double x2, double y2 );
```

其中用户传入的参数为平面上两个点的坐标(`x1`, `y1`)和(`x2`, `y2`)，函数`dist`应返回两点间的距离。

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <math.h>

double dist( double x1, double y1, double x2, double y2 );

int main()
{    
    double x1, y1, x2, y2;

    scanf("%lf %lf %lf %lf", &x1, &y1, &x2, &y2);
    printf("dist = %.2f\n", dist(x1, y1, x2, y2));
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
10 10 200 100
```

**输出样例：**

```
dist = 210.24
```

**输入样例：**

```properties
10 10 200 100
```

**输出样例：**

```
dist = 210.24
```

**题解：**

```c
double dist( double x1, double y1, double x2, double y2 ){
  return sqrt(pow(y1-y2,2)+pow(x1-x2,2));
}
```

## 符号函数

本题要求实现符号函数sign(x)

**函数接口定义：**

```c
int sign( int x );
```

其中`x`是用户传入的整型参数。符号函数的定义为：若`x`大于0，`sign(x)` = 1；若`x`等于0，`sign(x)` = 0；否则，`sign(x)` = −1。

**裁判测试程序样例：**

```c
#include <stdio.h>

int sign( int x );

int main()
{
    int x;

    scanf("%d", &x);
    printf("sign(%d) = %d\n", x, sign(x));
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
10
```

**输出样例：**

```
sign(10) = 1
```

**题解：**

```c
int sign(int x){
  if(x>0)return 1;
  if(x<0)return -1;
  if(!x)return 0;
}
```

## 使用函数求1到10的阶乘和

本题要求实现一个计算非负整数阶乘的简单函数，使得可以利用该函数，计算1!+2!+⋯+10!的值。

**函数接口定义：**

```c
double fact( int n );
```

其中`n`是用户传入的参数，其值不超过10。如果`n`是非负整数，则该函数必须返回`n`的阶乘。

**裁判测试程序样例：**

```c
#include <stdio.h>

double fact( int n );

int main(void)
{    
    int i;
    double sum; 

    sum = 0; 
    for(i = 1; i <= 10; i++) 
        sum = sum + fact(i); 
        
    printf("1!+2!+...+10! = %f\n", sum); 
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```
本题没有输入
```

**输出样例：**

```
1!+2!+...+10! = 4037913.000000
```

**题解：**

```c
double fact(int n){     					//这题梦幻的一匹？？？
  if(n==1)return 1;
  return n*fact(n-1);
}
```

## **使用函数判断完全平方数**

本题要求实现一个判断整数是否为完全平方数的简单函数。

**函数接口定义：**

```c
int IsSquare( int n );
```

其中`n`是用户传入的参数，在长整型范围内。如果`n`是完全平方数，则函数`IsSquare`必须返回1，否则返回0。

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <math.h>

int IsSquare( int n );

int main()
{
    int n;
    
    scanf("%d", &n);
    if ( IsSquare(n) ) printf("YES\n");
    else printf("NO\n");
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例1：**

```properties
90
```

**输出样例1：**

```
NO
```

**输入样例2：**

```
100
```

**输出样例2：**

```
YES
```

**题解：**

```c
int IsSquare( int n ){
  if(n==(int)(sqrt(n)*(int)(sqrt(n))))return 1;
  else return 0;
}
```

## **使用函数求素数和**

本题要求实现一个判断素数的简单函数、以及利用该函数计算给定区间内素数和的函数。

素数就是只能被1和自身整除的正整数。注意：1不是素数，2是素数。

**函数接口定义：**

```c
int prime( int p );
int PrimeSum( int m, int n );
```

其中函数`prime`当用户传入参数`p`为素数时返回1，否则返回0；

函数`PrimeSum`返回区间\[`m`, `n`]内所有素数的和。题目保证用户传入的参数`m`≤`n`。

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <math.h>

int prime( int p );
int PrimeSum( int m, int n );
    
int main()
{
    int m, n, p;

    scanf("%d %d", &m, &n);
    printf("Sum of ( ");
    for( p=m; p<=n; p++ ) {
        if( prime(p) != 0 )
            printf("%d ", p);
    }
    printf(") = %d\n", PrimeSum(m, n));

    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
-1 10
```

**输出样例：**

```
Sum of ( 2 3 5 7 ) = 17
```

**题解：**

```c
int prime( int p ){
    if(p<2)return 0;
    int k=sqrt(p);
    if(p==2)return 1;
    for(int i=2;i<=k;i++)
      if(!(p%i))return 0;
    return 1;
}
int PrimeSum( int m, int n ){
  int sum=0;
  if(m<2)m==2;
    for(int i=m;i<=n;i++){
      if(prime(i)==1)
        sum+=i;
    }
    return sum;
}
```

## **数字金字塔**

本题要求实现函数输出n行数字金字塔。

**函数接口定义：**

```c
void pyramid( int n );
```

其中`n`是用户传入的参数，为\[1, 9]的正整数。要求函数按照如样例所示的格式打印出`n`行数字金字塔。

注意每个数字后面跟一个空格。

**裁判测试程序样例：**

```c
#include <stdio.h>

void pyramid( int n );

int main()
{    
    int n;

    scanf("%d", &n);
    pyramid(n);
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
5
```

**输出样例：**

```
    1 
   2 2 
  3 3 3 
 4 4 4 4 
5 5 5 5 5
```

**题解：**

```c
void pyramid( int n ){
    
  for(int i=1;i<=n;i++){    //第i行
      
    for(int k=i;k<n;k++)          //第i行输入i-1个空格
        printf(" ");
       
    for(int j=1;j<=i;j++)    //第i行输入i个i
      printf("%d ",i);
    
    printf("\n");			//换行
      
  }
    
}
```

## **使用函数计算两个复数之积**

若两个复数分别为：`c1=x1+y1i`和`c2=x2+y2i`，则它们的乘积为`c1×c2=(x1x2−y1y2)+(x1y2+x2y1)i`。

本题要求实现一个函数计算两个复数之积。

**函数接口定义：**

```c
double result_real, result_imag;
void complex_prod( double x1, double y1, double x2, double y2 );
```

其中用户传入的参数为两个复数`x1`+`y1`\_i\_和`x2`+`y2`_i_；函数`complex_prod`应将计算结果的实部存放在全局变量`result_real`中、虚部存放在全局变量`result_imag`中。

**裁判测试程序样例：**

```c
#include<stdio.h> 

double result_real, result_imag;
void complex_prod( double x1, double y1, double x2, double y2 );

int main(void) 
{ 
    double imag1, imag2, real1, real2;    

    scanf("%lf %lf", &real1, &imag1);             
    scanf("%lf %lf", &real2, &imag2);             
    complex_prod(real1, imag1, real2, imag2);     
    printf("product of complex is (%f)+(%f)i\n", result_real, result_imag);
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
1 2
-2 -3
```

**输出样例：**

```
product of complex is (4.000000)+(-7.000000)i
```

**题解：**

```c
void complex_prod( double x1, double y1, double x2, double y2 ){
    result_real=x1*x2-y1*y2;
    result_imag=x1*y2+x2*y1;
}
```

## **使用函数求最大公约数**

本题要求实现一个计算两个数的最大公约数的简单函数。

**函数接口定义：**

```c
int gcd( int x, int y );
```

其中`x`和`y`是两个正整数，函数`gcd`应返回这两个数的最大公约数。

**裁判测试程序样例：**

```c
#include <stdio.h>

int gcd( int x, int y );

int main()
{
    int x, y;
    
    scanf("%d %d", &x, &y);
    printf("%d\n", gcd(x, y));
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
32 72
```

**输出样例：**

```
8
```

**题解：**

## **使用函数统计指定数字的个数**

本题要求实现一个统计整数中指定数字的个数的简单函数。

**函数接口定义：**

```c
int CountDigit( int number, int digit );
```

其中`number`是不超过长整型的整数，`digit`为\[0, 9]区间内的整数。函数`CountDigit`应返回`number`中`digit`出现的次数。

**裁判测试程序样例：**

```c
#include <stdio.h>

int CountDigit( int number, int digit );
    
int main()
{
    int number, digit;

    scanf("%d %d", &number, &digit);
    printf("Number of digit %d in %d: %d\n", digit, number, CountDigit(number, digit));
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
-21252 2
```

**输出样例：**

```
Number of digit 2 in -21252: 3
```

**题解：**

```c
int CountDigit( int number, int digit ){
  int count=0;
  if(number<0)number=-number;
  if(!number&&!digit)return 1;
  while(number){
    if(number%10==digit)
        count++;
    number/=10;
  }
    return count;
}
```

## **使用函数求余弦函数的近似值**

本题要求实现一个函数，用下列公式求cos(_x_)的近似值，精确到最后一项的绝对值小于`e`：

`cos(x)=x^0/0!−x^2/2!+x^4/4!−x^6/6!+⋯`

**函数接口定义：**

```c
double funcos( double e, double x );
```

其中用户传入的参数为误差上限`e`和自变量`x`；函数`funcos`应返回用给定公式计算出来、并且满足误差要求的`cos(x)`的近似值。

输入输出均在双精度范围内。

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <math.h>

double funcos( double e, double x );

int main()
{    
    double e, x;

    scanf("%lf %lf", &e, &x);
    printf("cos(%.2f) = %.6f\n", x, funcos(e, x));
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
0.01 -3.14
```

**输出样例：**

```
cos(-3.14) = -0.999899
```

**题解：**

## **统计某类完全平方数**

本题要求实现一个函数，判断任一给定整数`N`是否满足条件：它是完全平方数，又至少有两位数字相同，如144、676等。

**函数接口定义：**

```c
int IsTheNumber ( const int N );
```

其中`N`是用户传入的参数。如果`N`满足条件，则该函数必须返回1，否则返回0。

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <math.h>

int IsTheNumber ( const int N );

int main()
{
    int n1, n2, i, cnt;
    
    scanf("%d %d", &n1, &n2);
    cnt = 0;
    for ( i=n1; i<=n2; i++ ) {
        if ( IsTheNumber(i) )
            cnt++;
    }
    printf("cnt = %d\n", cnt);

    return 0;
}

/* 你的代码将被嵌在这里 */
```

**输入样例：**

```properties
105 500
```

**输出样例：**

```
cnt = 6
```

**题解：**

```c
/* 你的代码将被嵌在这里 */
int IsTheNumber ( const int N ){
    int a[100];
    int i=1;
    int n=N;
    while(n){               ///////////////////
        a[i]=n%10;          //把N倒序存入数组a
        n/=10;
        i++;
    }                       ///////////////////
    for(;i;i--){
        for(int j=i-1;j;j--){
            if(a[i]==a[j]){
                if(N== (int)(sqrt(N))*(int)(sqrt(N)) ){
                    return 1;
                }
            }
        }
    }
    return 0;
}
```

## 【函数的指针参数】交换2个实数

用指针变量作为函数形参，编写函数实现2个实数的交换

**函数接口定义：**

```
void mySwap(double*,double*);
```

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <math.h>

void mySwap(double*,double*);

int main()
{
    double a,b;
    while(scanf("%lf%lf",&a,&b)!=EOF){
        mySwap(&a,&b);
        printf("%.2f %.2f\n",a,b);
    }
    return 0;
}
```

**输入**

```
测试数据有多组，处理到输入结束
```

**输出**

```
输出交换后的2个实数，保留2位小数。
每个输出占1行
```

**样例输入**

```
3.5 5.25
5 3
```

**样例输出**

```
5.25 3.50
3.00 5.00
```

**题解：**

```c
void mySwap(double* m,double* n){
    double t;
    t=*m;
    *m=*n;
    *n=t;
}
```

## 【函数的指针参数】数组排序

**题目描述**

使用自定义函数

```c
void sort(int *a, int n);
```

对数组a中的整数进行排序（升序）

函数的参数：a为数组（指针），n为数组中元素的个数。

**裁判程序如下：**

```c
#include <stdio.h>
#define N (10+5)
void sort(int *a, int n);
int main(){
    int i,n=0,a[N];
    while(scanf("%d",&a[n])!=EOF)n++;
    sort(a,n);
    for(int i=0;i<n;i++)
        printf("%d\n",a[i]);
}
```

**输入**

```
一组整数（不超过10个），每个整数的绝对值不超过1000，读取到输入结束
```

**输出**

```
按升序输出，每行一个
```

**样例输入**

```
3 1 4 1 5 9
```

**样例输出**

```
1
1
3
4
5
9
```

**题解：**

```c
void sort(int *a, int n){
    for(int i=0;i<n;i++){
        for(int j=0;j<i-n-1;j++){
            if(*(a+j)>*(a+j+1)){
                int t=*(a+j);
                *(a+j)=*(a+j+1);
                *(a+j+1)=t;
            }
        }
    }
}
```

## 星星球

**题目描述**

```
蚂蚁庄园里的星星球游戏，大部分人都接触过。看好友榜单里，大家的分数都很高，但是这些分数需要多少次点击组合才能实现呢？

星星球得分规则：

在球落地前，颜色显示为白色的时候点击，得五分；

在球落地前，颜色显示为蓝色的时候点击，得八分；

在球落地前，颜色显示为黄色的时候点击，得十分；

在球落地后，游戏结束。

总有人无聊想知道得到分数n，需要点击多少次白色状态、多少次蓝色状态、多少次黄色状态，并且控制点击次数在m次以内（包括m）。

你能设计个程序帮他计算一下吗？如果无解，输出-1；如果有解，输出有几种解的方法能满足条件。
```

![](http://wlacm.com/upload/pimg1588\_1.png#id=drdJz\&originHeight=338\&originWidth=784\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

**输入**

```
两个整数n和m，n代表得到的分数（1≤n≤5000），m代表点击次数（1≤m≤500）
```

**输出**

```
输出解的个数
```

**样例输入**

```
【测试样例1】
50 20
【测试样例2】
50 5
【测试样例3】
50 2
```

**样例输出**

```
【测试样例1】
8
【测试样例2】
1
【测试样例3】
-1
```

**提示**

对于样例，需要得到50分，总共有8种方法

![](http://wlacm.com/upload/pimg1588\_2.png#id=oBOIu\&originHeight=293\&originWidth=703\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

对于样例1，总点击次数不能超过20次，所以有8种方案，输出8； 对于样例2，总点击次数不能超过5次，所以有1种方案，输出1； 对于样例3，总点击次数不能超过2次，所以有0种方案，输出-1。

**题解：**

## 合并整数

**题目描述**

有n个整数，相同的两个整数可以合并成一个更大的整数。合并可以一直进行下去，直到没有相同的整数为止

请求出合并完成后最大的整数

**输入**

第一行给定一个整数n（1≤n≤1000），第二行给定n个空格分割的整数x（1≤x≤1000）

**输出**

输出合并完成后最大的整数

\*\*样例输入 \*\*

```
9
3 5 7 12 13 5 20 7 14
```

**样例输出**

```
28
```

**提示**

```
第一步，5和5合并成10，得到整数数列3 10 7 12 13 20 7 14
第二步，7和7合并成14，得到整数数列3 10 14 12 13 20 14
第三步，14和14合并成28，得到整数数列3 10 28 12 13 20
```

**题解：**

```c
#include <stdio.h>
#include <math.h>
void sort(int *f,int n);
int main(){ 
	int n,a[10000];
	scanf("%d",&n);
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
	
	
	while(1){
		sort(a,n);
		int flag=0;
		for(int i=0;i<n-1;i++){
			if(a[i]==a[i+1]&&a[i]!=-1){						
				a[i]+=a[i];						
				a[i+1]=-1;
				flag=1;
				break;
			}
		}
		if(!flag)break;
		
	}
	sort(a,n);
	printf("%d",a[n-1]);
	
	return 0;
} 
void sort(int *a,int n){
	for(int i=0;i<n;i++){
		for(int j=0;j<n-i-1;j++){
			if(a[j]>a[j+1]){
				int t=a[j];
				a[j]=a[j+1];
				a[j+1]=t;
			}
		}
	}
}
```

## 【函数的指针参数】日期问题

**题目描述**

输入年和天数，输出对应的月和日。例如：输入2000和61，输出3和1。

**函数接口定义**：

```
void month_day(int,int,int*,int*);
```

**裁判测试程序样例：**

```c
#include <stdio.h>
#include <stdlib.h> 
#include <time.h> 

void month_day(int,int,int*,int*);

int main( )
{   
    int d,m,y,yd;
    while(scanf("%d%d",&y,&yd)!=EOF){
        month_day(y,yd,&m,&d);
        printf("%d-%d\n",m,d);
    }
}
```

**输入**

输入年和天数；测试数据有多组，处理到输入结束。

**输出**

输出对应的月和日。

每个输出占1行。

**样例输入**

```
2010 1
2010 32
```

**样例输出**

```
1-1
2-1
```

**题解：**

```c
void month_day(int year,int yearday,int *pmonth,int *pday){
    int pd,i;
    int tab[2][13]={
        {0,31,28,31,30,31,30,31,31,30,31,30,31},
        {0,31,29,31,30,31,30,31,31,30,31,30,31}
    };
    pd=(year%400==0||(year%4==0&&year%100!=0)); 
    for(i=0;yearday>tab[pd][i];i++)
        yearday=yearday-tab[pd][i];
    *pmonth=i;
    *pday=yearday;
}
```

## 【函数的指针参数】自定义字符串长度函数 my\_strlen

**题目描述**

```
编写自定义函数int my_strlen(char* s); 检测字符串s的长度
```

**特别提示：不允许使用“string.h”中的strlen函数。**

**裁判程序如下：**

```c
#include <stdio.h>
int my_strlen(char* s);
int main()
{    
    char s[105];
    while(gets(s)){
        int n=my_strlen(s);
        printf("%d\n",n);
    }
    return 0;
}
```

**输入**

一行字符串（长度不超过100）

**输出**

字符串的长度

**样例输入**

```
abc
how are you?
```

**样例输出**

```
3
12
```

**题解：**

```c
int my_strlen(char* s){
    char *t=s;
    while(*s)s++;
    return s-t;
}
```

## 【字符串函数】ispalindrome

**题目描述**

```
编写自定义函数int ispalindrome(char* s); 
检测字符串s是否为回文（所谓回文字符串,就是一个字符串,从左到右读和从右到左读是完全一样的）
如果s为回文，函数返回值为1，否则返回值为0
输入abc，输出no
输入rotator，输出yes
```

**裁判测试程序如下：**

```c
#include <stdio.h>
#include<string.h>
int ispalindrome(char* s);
int main()
{    
    char s[105];
    gets(s);
    if(ispalindrome(s))printf("yes");
    else printf("no");
    return 0;
}
```

**输入**

```
一行字符串（长度不超过100）
```

**输出**

```
如果输入字符串为回文，则输出yes
否则输出no
```

**样例输入**

```
rotator
```

**样例输出**

```
yes
```

**题解：**

```c
int ispalindrome(char* s){
    for(int i=0,j=strlen(s)-1-i;i<j;i++,j--)
        if(*(s+i)!=*(s+j))return 0;
        else break;
    
    return 1;
}
```

## 【函数的指针参题目描述

本题要求编写函数，将输入字符串t中从第m个字符开始的全部字符复制到字符串s中。

**函数接口定义：**

```c
void strmcpy( char *t, int m, char *s );
```

函数`strmcpy`将输入字符串`char *t`中从第m个字符开始的全部字符复制到字符串`char *s`中。

若m超过输入字符串的长度，则结果字符串应为空串。

**输入**

输入m和字符串t，字符串长度不超过20个字符

**输出**

输出复制后的字符串

**样例输入**

```
7
happy new year
```

**样例输出**

```
new year
```

**题解：**

```c
void strmcpy( char *t, int m, char *s ){
    int i=0,j=0;
    for(i=0;i<105;i++)
        if(*(t+i))
            j++;
        else 
            break;
    
    for(i=0;i<j;i++)
        if(m<=j)
            *(s+i)=*(t+m-1+i);
        else 
            *(s+i)='\0';
}
```

## 手机

**题目描述**

一般的手机的键盘是这样的：

![](https://cdn.luogu.com.cn/upload/image\_hosting/2mokuz5x.png#id=XvVc9\&originHeight=218\&originWidth=263\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

要按出英文字母就必须要按数字键多下。

例如要按出 `x` 就得按 9 两下，第一下会出 `w`，而第二下会把 `w` 变成 `x`。0 键按一下会出一个空格。

你的任务是读取若干句只包含英文小写字母和空格的句子，求出要在手机上打出这个句子至少需要按多少下键盘。

**输入格式**

一行句子，只包含英文小写字母和空格，且不超过 200 个字符。

**输出格式**

一行一个整数，表示按键盘的总次数。

**样例**

**样例输入**

```
i have a dream
```

**样例输出**

```
23
```

**提示**

NOI导刊2010普及（10）

**题解：**

链接：[https://ac.nowcoder.com/acm/contest/11227/B](https://ac.nowcoder.com/acm/contest/11227/B)\
来源：牛客网

## 减法和除法

鸡尾酒的学生丹丹分不清除法和减法，因为他觉得两种运算都是将一个数字变小，所以都差不多。

为了让丹丹能够更好地理解除法和减法，鸡尾酒给了他这样一个问题：

给定一个正整数 `n`，每次有两种操作：

1. 使得这个数字除以 `2`（由于丹丹没学过小数和分数，所以这里是除法是整除，向下取整）
2. 将这个数字减去一个给定值 `x`。

问最少几次操作可以将这个数字变成一个小于等于零的数字。

由于丹丹从未接触过负数，所以根本不知道小于等于零的数字是什么，你可以帮帮他吗？

**输入描述:**

```
给定两个正整数 n,x(1≤n,x≤109)n,x(1 \leq n,x \leq 10^9)n,x(1≤n,x≤109)
```

**输出描述:**

```
输出一行一个整数表示答案
```

**输入**

```
30 5
```

**输出**

```
4
```

**说明**

```
先进行一次操作 1，得到 15，再进行三次操作 2（即减去 5），此时得到 0。或者先进行两次操作 1，得到 7，再进行两次操作 2，得到 -2。这两种方案都是 4 次操作。
```

**题解：**

```c
#include<stdio.h>
int min(int a,int b);
int main(){					//由于减法和除法都是将数字变小，而我们的目标就是将数字变得尽可能地小，    				
    int n,x,i=0;			//所以我们可以去判断到底哪一种操作会使得数字变得更小，来使用对应的运算符。
    scanf("%d %d",&n,&x);
    while(n>0){
        n=min(n/2,n-x);
        i++;
    }
    printf("%d",i);
    return 0;
}
int min(int a,int b){
    if(a>b)
        return b;
    else return a;
}
```

## 【结构体】成绩统计

**题目描述**

有10个学生，每个学生的数据包括学号、姓名、3门课程的成绩。读入这10个学生的数据，要求输出3门课程的总平均成绩，以及个人平均分最高的学生的数据（包括学号、姓名、3门课程成绩、平均分数）。

**输入**

共有10行，每行包含了一个学生的学号（整数）、名字（长度不超过19的无空格字符串）和3门课程的成绩（0至100之间的整数），用空格隔开。

**输出**

第一行包含了3个实数，分别表示3门课程的总平均成绩，保留2位小数，每个数之后输出一个空格。\
第二行输出个人平均分最高的学生的数据，与输入数据格式相同。如果有多位个人平均分最高的学生，输出按照输入顺序第一个最高分的学生数据。\
请注意行尾输出换行。

**样例输入**

```
101 AAA 80 81 82
102 BBB 83 84 85
103 CCC 86 87 88
104 DDD 89 90 91
105 EEE 92 93 94
106 FFF 80 90 100
107 GGG 85 90 95
108 HHH 80 85 90
109 III 90 91 92
110 JJJ 91 88 87
```

**样例输出**

```
85.60 87.90 90.40 
105 EEE 92 93 94
```

**题解：**

```c
#include<stdio.h>
#include<string.h>

int main(){
	int n;
	float sum1=0,sum2=0,sum3=0;
	struct student{
		int id;
		char name[100];
		int grade[3];
		float ave;
	}stu[10];
	
	for(int i=0;i<10;i++){
		scanf("%d %s %d %d %d",&stu[i].id,&stu[i].name,&stu[i].grade[0],&stu[i].grade[1],&stu[i].grade[2]);
	
		for(int k=0;k<3;k++)					
			stu[i].ave+=stu[i].grade[k]*1.0/3;		//ave是个人平均分
		
		sum1+=stu[i].grade[0]/10.0;
		sum2+=stu[i].grade[1]/10.0;
		sum3+=stu[i].grade[2]/10.0;

		
	}
	float max=0;
	int k=0;
	for(int i=0;i<10;i++)
		if(stu[k].ave<stu[i].ave)k=i;
	
	
	printf("%.2f %.2f %.2f\n",sum1,sum2,sum3);
	printf("%d %s %d %d %d",stu[k].id,stu[k].name,stu[k].grade[0],stu[k].grade[1],stu[k].grade[2]);
	return 0;
}
```

## 学生成绩排序

**题目描述**

输入一组学生的成绩，按照成绩降序输出成绩表。如有相同成绩，较小的学号排位靠前

**输入**

输入格式为每行两个数值，学号N为10位数字，成绩S取值为整数（0≤S≤100）

读取输入直到输入结束（数据总量不超过50行，且不会出现重复的学号）

**输出**

输出格式为每行两个数值，学号N之后有一个空格，成绩值的输出宽度占3个位置

**样例输入**

```
2017010405 78
2017010426 80
2017010402 61
2017010377 95
2017010427 80
```

**样例输出**

```
2017010377  95
2017010426  80
2017010427  80
2017010405  78
2017010402  61
```

**题解：**

```c
#include<stdio.h>
#include<string.h>

int main(){
	typedef struct student{
		int n;
		int s;
	}STU;
	STU stu[50],t;
	int i=0;
	while(scanf("%d %d",&stu[i].n,&stu[i].s)!=EOF)i++;
	//printf("%d\n",i);
	int count=i-1;
		for(int k=0;k<count+1;k++){
			for(int j=0;j<count-k;j++){
				if(stu[j].s < stu[j+1].s){
					t = stu[j];
					stu[j] = stu[j+1];
					stu[j+1] = t;
				}
			}
		}
		for(int k=0;k<count+1;k++){
			for(int j=0;j<count-k;j++){
				if(stu[j].s == stu[j+1].s&&stu[j].n > stu[j+1].n){
					t = stu[j];
					stu[j] = stu[j+1];
					stu[j+1] = t;
				}
			}
		}
		for(i=0;i<count+1;i++)
			printf("%d %3d\n",stu[i].n,stu[i].s);
	
	return 0;
}
```

## 【结构体】日期统计

**题目描述**

定义一个包括年、月、日的结构体变量，读入年、月、日，计算该日在当年中是第几天。注意闰年问题。

**输入**

三个整数，分别表示年、月、日。保证输入是实际存在的日期，且年份在1000至3000之间（包含1000和3000）。

**输出**

输出该日期是一年中的第几天。

请注意行尾输出换行。

**样例输入**

```
2012 12 21
```

**样例输出**

```
356
```

**题解：**

```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    
    struct student {
        int year;
        int month;
        int day;
    }stu;
    int sum=0;
    int tab[2][13]={
        {0,31,28,31,30,31,30,31,31,30,31,30,31},//非闰年[0]
        {0,31,29,31,30,31,30,31,31,30,31,30,31}//闰年[1
    };
    
    scanf("%d%d%d",&stu.year,&stu.month,&stu.day);
    int pd=(stu.year%400==0||(stu.year%4==0&&stu.year%100!=0));//闰年为1，非闰年为0
    if(stu.month==1){
        printf("%d",stu.day);
        return 0;
    }
    for(int i=0;i<stu.month;i++){
        sum+=tab[pd][i];
    }
    printf("%d",sum+stu.day);
    return 0;
}
```

```c
#include<iostream>
#include<algorithm>
using namespace std;
int a[2][1000]={
    {0,31,28,31,30,31,30,31,31,30,31,30,31},
    {0,31,29,31,30,31,30,31,31,30,31,30,31},
};
int sum=0;
bool dp;
int main(){
    int y,m,d;
    while(cin>>y>>m>>d){
        sum=0;
        dp=((y%4==0 && y%100)|| y%400==0);
        if(m==1){
            cout<<d<<endl;
            continue;
        }
        for(int i=0;i<m;i++)
            sum+=a[dp][i];
        cout<<sum+d<<endl;
    }
    return 0;
}
```

## 晨跑次数统计

**题目描述**

某学校为鼓励学生锻炼身体，要求学生周一到周五早晨在操场跑步，并进行刷卡记录，作为期末评优的依据。

刷卡机器中记录的数据格式为学号和刷卡时间，其中学号`N`为`10`位数字，时间`T`格式为`yyyymmddhhmmss`

读卡程序确保每天不会多次记录同一名学生的晨跑刷卡时间

要求：根据刷卡机器中记录的学生刷卡记录，按照学号升序统计学生晨跑次数

**输入**

输入格式为每行两个数值，学号N与时间T之间有一个空格 。

读取输入直到输入结束（数据总量不超过1000行）

**输出**

输出格式为每行两个数值，学号以及相应的晨跑次数，两者之间有一个空格。

**样例输入**

```
2015016932 20160311065532
2015017890 20160409070156
2015019860 20160329063051
2015019860 20160305065217
2015018745 20160305065656
```

**样例输出**

```
2015016932 1
2015017890 1
2015018745 1
2015019860 2
```

**题解：**

```c
#include<stdio.h>
#include<string.h>
int main(){
	typedef struct student{
		int n;
		long long int T;
        int times;
	}STU;
	STU stu[1000]={0,0,0};
	int i=0,k=0;

    while(scanf("%d %lld",&stu[i].n,&stu[i].T)!=EOF)i++;
    int count=i;
    for(i=0;i<count;i++){
        for(k=0;k<count-1-i;k++){
            if(stu[k].n>stu[k+1].n){
                int t=stu[k].n;
                stu[k].n=stu[k+1].n;
                stu[k+1].n=t;
            }
        }
    }
    int flag=0;
    for(i=0;i<count;i++){
        for(k=i+1;k<count;k++){
            if(stu[i].n==stu[k].n){
                stu[i].times++;
                stu[k].n=0;
            }
        }
        if(stu[i].n)
            printf("%d %lld\n",stu[i].n,stu[i].times+1);
    }

	return 0;
}
```

## IDENTITY V

Yuki最近迷上了一款叫作IDENTITY V（第五人格）的游戏，六一节快到了，游戏也推出了一个活动。在活动期间，使用不同的角色参与对战，根据玩家在该局游戏中的表现会给予该角色相应的演绎积分，当演绎积分到达2000时，可以兑换相应角色的动态头像。该游戏现有的典型角色如下：

![](http://wlacm.com/upload/pimg1589\_1.png#id=ww8XO\&originHeight=392\&originWidth=537\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

Yuki十分想要得到动态头像，每个玩家只能获得一个角色的动态头像，如果某一角色的积分足够，他会立即兑换。请根据Yuki在活动期间的对战情况，看看Yuki能够得到哪个角色的头像。

![](http://wlacm.com/upload/pimg1589\_2.png#id=UsPqQ\&originHeight=332\&originWidth=654\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

**输入**

第一行输入一个数T（T≤7），表示Yuki玩这个游戏的天数。接下来是T组数据。

每组数据的第一行是一个整数n（n≤20），表示当天玩的局数，接下来是n行数据，每行数据中包含一个字符串s（长度不超过20）代表Yuki当局使用的角色和一个整数g（g<1000）表示Yuki获得的演绎值。

**输出**

如果Yuki能够获得某一角色的所有奖励，则将该角色输出；如果不能获得任何角色的奖励，则输出“NOTHING”（不包含引号）

**样例输入**

```
【测试样例1】
5
2
Doctor 500
Gardener 600
2
Doctor 500
Gardener 600
3
Machinist 600
Doctor 500
Machinist 800
1
Doctor 500
1
Machinist 800

【测试样例2，请注意这一组的角色名称】
3 
2
ZXY 900
YWH 500
1
CXW 400
1
WSY 600
```

**样例输出**

```
【测试样例1】
Doctor

【测试样例2】
NOTHING
```

**题解：**

```c
#include<stdio.h>
#include<string.h>
int main(){
	typedef struct student{
		char name[35];
		int grade;
	}STU;
	STU stu[1000];
	int n,T,t=0;
	int sum=0;
	scanf("%d",&n);
	for(int i=0;i<n;i++){
		scanf("%d",&T);
		for(int k=0;k<T;k++){
			scanf("%s %d",stu[t].name,&stu[t].grade);
			t++;
		}
	}
	
	for(int i=0;i<t;i++){
		sum=stu[i].grade;
		for(int k=0;k<i;k++){
			if(!strcmp(stu[i].name,stu[k].name)){
				sum+=stu[k].grade;
			}
		}
		if(sum>=2000){
			printf("%s",stu[i].name);
			return 0;
		}
	}
	printf("NOTHING");
	return 0;
}
```

## 性感素数

“[性感素数](http://mathworld.wolfram.com/SexyPrimes.html) ”是指形如 `(p,p+6)` 这样的一对素数。

之所以叫这个名字，是因为拉丁语管`六`叫`sex`（即英语的“性感”）。

现给定一个整数，请你判断其是否为一个性感素数。

**输入格式**

输入在一行中给出一个正整数 `N`。

**输出格式**

若 `N` 是一个性感素数，则在一行中输出 `Yes`，并在第二行输出与`N`配对的另一个性感素数（若这样的数不唯一，输出较小的那个）。

若 NN 不是性感素数，则在一行中输出 `No`，然后在第二行输出大于`N`的最小性感素数。

**输入样例**1：

```
47
```

**输出样例**1：

```
Yes
41
```

输入样例2：

```
21
```

**输出样例**2：

```
No
23
```

**题解：**

```c
#include<stdio.h>
#include<math.h>
int isPrime(int n);
int main(){
    int n;
    scanf("%d",&n);
    if(isPrime(n)&&(isPrime(n+6)||isPrime(n-6))){
		printf("Yes\n");
		if(isPrime(n-6))
			printf("%d",n-6);
		else
			printf("%d",n+6);
		
	}else{
		printf("No\n");
		for(int i=n+1;;i++){
			if(isPrime(i)&&(isPrime(i+6)||isPrime(i-6))){
				printf("%d",i);
				return 0;
			}
		}
	}
		
    return 0;
}
int isPrime(int n){
	if(n<=1)return 0;
    int k=sqrt(n*1.0);
    if(n==2)return 1;
    for(int i=2;i<=k;i++)
        if(!(n%i))
			return 0;
    return 1;
}
	/*if(!isPrime(n)){
		printf("No\n");
		while(!isPrime(n)){
			if(isPrime(n)){
				printf("%d",n);
				return 0;
			}
			n++;
		}
	}*/
```

## 菱形图案

**题目描述**

从键盘输入一个整数n(1≤n≤30)，打印出指定的菱形。

**输入**

正整数n（1≤n≤30）。

**输出**

指定的菱形。

第一行前面有n-1个空格，第二行有n-2个空格，以此类推。

**样例输入**

```
3
```

**样例输出**

```
  *
 ***
*****
 ***
  *
```

**题解：**

```c
#include<stdio.h>
#include<string.h>
int main(){
    int n,i,j,m,t;
    scanf("%d",&n);
        for(i=1;i<=n;i++){
            for(j=i;j<=n-1;j++)
                printf(" ");
            for(m=1;m<=2*i-1;m++)
                printf("*");
            printf("\n");
        }
        j=1;
        for(m-=1;m>=1;){
            m-=2;
            for(i=1;i<=j;i++)
                printf(" ");
            for(t=1;t<=m;t++)
                printf("*");
            printf("\n");
            j++;
        }
	return 0;
}
```

## Counterclockwise Rotation

**Problem Statement**

In an _x_ _y_-coordinate plane whose x\_x\_-axis is oriented to the right and whose y\_-axis is oriented upwards, rotate a point (_a_,_b_) around the origin d\_ degrees counterclockwise and find the new coordinates of the point.

**Constraints**

* −1000≤\_a\_,\_b\_≤1000
* 1≤\_d\_≤360
* All values in input are integers.

***

**Input**

Input is given from Standard Input in the following format:

```
a b d
```

**Output**

Let the new coordinates of the point be (_a_′,_b_′). Print _a_′ and _b_′ in this order, with a space in between.\
Your output will be considered correct when, for each value printed, the absolute or relative error from the answer is at most 10^-6.

***

**Sample Input 1**

```
2 2 180
```

**Sample Output 1**

```
-2 -2
```

When (2,2) is rotated around the origin 180180 degrees counterclockwise, it becomes the symmetric point of (2,2) with respect to the origin, which is (−2,−2).

***

**Sample Input 2**

```
5 0 120
```

**Sample Output 2**

```
-2.49999999999999911182 4.33012701892219364908
```

When (5,0) is rotated around the origin 120120 degrees counterclockwise, it becomes (-5/2 , 5\sqrt(3)/2)(−25,253).\
This sample output does not precisely match these values, but the errors are small enough to be considered correct.

***

**Sample Input 3**

```
0 0 11
```

**Sample Output 3**

```
0.00000000000000000000 0.00000000000000000000
```

Since (_a_,_b_) is the origin (the center of rotation), a rotation does not change its coordinates.

***

**Sample Input 4**

```
15 5 360
```

**Sample Output 4**

```
15.00000000000000177636 4.99999999999999555911
```

A 360-degree rotation does not change the coordinates of a point.

***

**Sample Input 5**

```
-505 191 278
```

**Sample Output 5**

```
118.85878514480690171240 526.66743699786547949770
```

**source code**

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
int main(){
    double a,b,d;
    double e,f;
    scanf("%lf %lf %lf",&a,&b,&d);
    d=d/180.0*acos(-1);
    printf("%.20lf %.20lf",a*cos(d)-b*sin(d),a*sin(d)+b*cos(d));
	return 0;
}
```

## 人见人爱A^B

**题目描述**

求A^B的最后三位数表示的整数

说明：A^B的含义是“A的B次方”

**Input**

输入数据包含多个测试实例，每个实例占一行，由两个正整数A和B组成（1<=A,B<=10000），如果A=0, B=0，则表示输入数据的结束，不做处理。

**Output**

对于每个测试实例，请输出A^B的最后三位表示的整数，每个输出占一行。

**Sample**

| **Input**  | **Output** |
| ---------- | ---------- |
| 2 3        | 8          |
| 12 6       | 984        |
| 6789 10000 | 1          |
| 0 0        |            |

**题解**

```c
#include <bits/stdc++.h>
using namespace std;								//3位数及以上的数的x次方结果后3位是相等的
int main(){											//6789*6789=46,090,521
     int a, b;										//789*789=622,521
     scanf("%d%d", &a, &b);
     while (a != 0 || b != 0){
         int s = 1;
         a %= 1000;
            for (int i = 0; i < b; i++){
                 s *= a;
                 s %= 1000;
     		}
         printf("%d\n", s);
         scanf("%d%d", &a, &b);
     }
     return 0;
}
```

## 人见人爱A+B

**题目描述**

HDOJ上面已经有10来道A+B的题目了，相信这些题目曾经是大家的最爱，希望今天的这个A+B能给大家带来好运，也希望这个题目能唤起大家对ACM曾经的热爱\
这个题目的A和B不是简单的整数，而是两个时间，A和B 都是由3个整数组成，分别表示时分秒，比如，假设A为34 45 56，就表示A所表示的时间是34小时 45分钟 56秒

**Input**

输入数据有多行组成，首先是一个整数N，表示测试实例的个数，然后是N行数据，每行有6个整数AH,AM,AS,BH,BM,BS，分别表示时间A和B所对应的时分秒。题目保证所有的数据合法

**Output**

对于每个测试实例，输出A+B，每个输出结果也是由时分秒3部分组成，同时也要满足时间的规则（即：分和秒的取值范围在0\~59），每个输出占一行，并且所有的部分都可以用32位整数表示

**Sample**

| **Input**         | **Output** |
| ----------------- | ---------- |
| 2                 | 5 7 9      |
| 1 2 3 4 5 6       | 47 9 30    |
| 34 45 56 12 23 34 |            |

**题解**

```c
#include <stdio.h>
#include<string.h>
int main()
{
    int AH,AM,AS,BH,BM,BS;
    int n;
    scanf("%d",&n);
    for(int i=1;i<=n;i++){
        scanf("%d %d %d %d %d %d",&AH,&AM,&AS,&BH,&BM,&BS);

        if(AS+BS>60)
            AM+=(AS+BS)/60;
        if(AM+BM>60)
            AH+=(AM+BM)/60;
        printf("%d %d %d\n",AH+BH,(AM+BM)%60,(AS+BS)%60);
    }
    return 0;
}
```

## sort

**题目描述**

给你n个整数，请按从大到小的顺序输出其中前m大的数。

**Input**

每组测试数据有两行，第一行有两个数`n,m(0<n,m<1000000)`，第二行包含n个各不相同，且都处于区间`[-500000,500000]`的整数。

**Output**

对每组测试数据按从大到小的顺序输出前m大的数。

**Sample**

| Input                     | Output   |
| ------------------------- | -------- |
| 5 3                       | 213 92 3 |
| 3   -35   92   213   -644 |          |

**source code**

```c
#include <bits/stdc++.h>
using namespace std;
const int N = 1e6 + 5;
const long long T = 1e10 + 50;
int n, m, a[N];
int main(){
	cin >> n >> m;
	for (int i = 0; i < n; i++)
		cin >> a[i];
	sort(a, a + n);
	for (int i = 1; i <= m; i++)
		cout << a[n - i] << " ";
	return 0;
}
```

## [CF1703A](https://codeforces.com/contest/1703/problem/A) YES or YES?

There is a string `s` of length `3`, consisting of uppercase and lowercase English letters. Check if it is equal to "YES" (without quotes), where each letter can be in any case. For example, "yES", "Yes", "yes" are all allowable.

**Input**

The first line of the input contains an integer `t` (1≤`t`≤1031≤`t`≤103) — the number of testcases.

The description of each test consists of one line containing one string `s` consisting of three characters. Each character of `s` is either an uppercase or lowercase English letter.

**Output**

For each test case, output "YES" (without quotes) if `s` satisfies the condition, and "NO" (without quotes) otherwise.

You can output "YES" and "NO" in any case (for example, strings "yES", "yes" and "Yes" will be recognized as a positive response).

**Example**

**Input**

```
10
YES
yES
yes
Yes
YeS
Noo
orZ
yEz
Yas
XES
```

**Output**

```
YES
YES
YES
YES
YES
NO
NO
NO
NO
NO
```

**source code**

```c
#include<stdio.h>
#include<ctype.h>
#include<string.h>
const int N=1e5+1;
int main()
{
	int n;
  	char c[N],a[]={"YES"};
  	scanf("%d\n",&n);
  	while(n--){
    gets(c);
    for(int i=0;i<strlen(c);i++)
        c[i]=toupper(c[i]);
    
    if(!strcmp(c,a))
        puts("YES");
    else puts("NO");
   }
  return 0;
}
```

[Problem - A - Codeforces](https://codeforces.com/contest/1703/problem/A)

## The area

Ignatius bought a land last week, but he didn't know the area of the land because the land is enclosed by a parabola and a straight line. The picture below shows the area. Now given all the intersectant points shows in the picture, can you tell Ignatius the area of the land?  Note: The point P1 in the picture is the vertex of the parabola.

![](https://vj.csgrandeur.cn/f9681ee11a167854dde398248a990558?v=1657865442#id=Br1LJ\&originHeight=216\&originWidth=219\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

**Input**

The input contains several test cases. The first line of the input is a single integer T which is the number of test cases. T test cases follow.\
Each test case contains three intersectant points which shows in the picture, they are given in the order of P1, P2, P3. Each point is described by two floating-point numbers X and Y(0.0<=X,Y<=1000.0).

**Output**

For each test case, you should output the area of the land, the result should be rounded to 2 decimal places.

**Sample**

| Input               | Output |
| ------------------- | ------ |
| 5.000000 5.000000   | 33.33  |
| 0.000000 0.000000   | 40.69  |
| 10.000000 0.000000  |        |
| 10.000000 10.000000 |        |
| 1.000000 1.000000   |        |
| 14.000000 8.222222  |        |

**source code**

```c
#include <stdio.h>
const int N=1e5+1;
int main(){
	int n;
	double x1,x2,y1,y2,x3,y3,s;
	scanf("%d",&n);
	while(n--){
		scanf("%lf %lf %lf %lf %lf %lf",&x1,&y1,&x2,&y2,&x3,&y3);
		s=-(y2-y1)/((x2-x1)*(x2-x1))*((x3-x2)*(x3-x2)*(x3-x2)/6);
		printf("%.2lf\n",s);
	}
	return 0;
}
```

## Number Sequence

A number sequence is defined as follows:

`f(1) = 1, f(2) = 1, f(n) = (A * f(n - 1) + B * f(n - 2)) mod 7`

Given A, B, and n, you are to calculate the value of f(n).

**Input**

The input consists of multiple test cases. Each test case contains 3 integers A, B and n on a single line (1 <= A, B <= 1000, 1 <= n <= 100,000,000). Three zeros signal the end of input and this test case is not to be processed.

**Output**

For each test case, print the value of f(n) on a single line.

**Sample**

| **Input** | **Output** |
| --------- | ---------- |
| 1 1 3     | 2          |
| 1 2 10    | 5          |
| 0 0 0     |            |

**source code**

```c
#include <stdio.h>
//
int fac(int ,int ,int );
int sum=0;
int main(){
	int a,b,n,i;
	int f[100]={0,1,1};
	while(~scanf("%d%d%d",&a,&b,&n)&&(a||b||n)){		//以0结束
		for(i=3;i<=49;i++)
			f[i]=(a*f[i-1]+b*f[i-2])%7;
		printf("%d\n",f[n%49]);
	}
	return 0;
}
```

## Fibonacci Again

There are another kind of Fibonacci numbers:

`F(0) = 7, F(1) = 11, F(n) = F(n-1) + F(n-2) (n>=2)`

**Input**

Input consists of a sequence of lines, each containing an integer `n`. (n < 1,000,000).

**Output**

Print the word "yes" if 3 divide evenly into `F(n)`.

Print the word "no" if not.

**Sample**

```c
Input	Output
0       no        
1       no         
2       yes        
3       no         
4       no         
5       no
```

**source code**

```c
#include <stdio.h>
const int N=1e5+1;
int main(){
	int a,b,n,i;
	
	while(~scanf("%d",&n)){
		if(n%4==2)
			printf("yes\n");
			else printf("no\n");
	}
	return 0;
}
```

## Rightmost Digit

Given a positive integer `N`, you should output the most right digit of `N^N`.

**Input**

The input contains several test cases. The first line of the input is a single integer `T`which is the number of test cases. `T`test cases follow.\
Each test case contains a single positive integer `N`(1<=N<=1,000,000,000).

**Output**

For each test case, you should output the rightmost digit of `N^N`.

**Sample**

```c
Input	Output
2		7
3		6
4
```

**source code**

```c
#include <stdio.h>
const int N=1e5+1;
int main(){
	long long n,sum,i,t;
	int T;
	scanf("%d",&T);

	while(T--){
		scanf("%lld",&n);
		sum=1;
		t=1;
		n%=20;
		if(!n)n=20;
		for(i=0;i<n;i++){
			sum=t*n;
			t=sum%10;
		}
		t%=10;
		printf("%lld\n",t);
	}
	return 0;
}
```

## 整除的尾数

一个整数，只知道前几位，不知道末二位，被另一个整数除尽了，那么该数的末二位该是什么呢？

**Input**

输入数据有若干组，每组数据包含二个整数`a`，`b`（0\<a<10000, 10\<b<100），若遇到`0 0`则处理结束。

**Output**

对应每组数据，将满足条件的所有尾数在一行内输出，格式见样本输出。同组数据的输出，其每个尾数之间空一格，行末没有空格。

**Sample**

```c
Input	 Output
200 40	 00 40 80
1992 95	 15
0 0
```

**source code**

```c
#include <stdio.h>
const int N=1e5+1;
int main(){
	int n,a,b,str[10000];
	int count=0;
	while(~scanf("%d %d",&a,&b)&&(a||b)){
		for(int i=0;i<100;i++){
			if((a*100+i)%b==0)
				str[count++]=i;
		}
		for(int i=0;i<count-1;i++)
			printf("%02d ",str[i]);
		printf("%02d\n",str[count-1]);
		count=0;
	}
	return 0;
}
```

## [nc37344-L ](https://ac.nowcoder.com/acm/contest/37344/L)HPU

**题目描述**

给定一个字符串，请你判断字符串中"HPU"的数目

**输入描述:**

一行，一个字符串 S ，字符串的长度 1≤∣S∣≤10^7

**输出描述:**

一行，输出字符串中"HPU"的数目

**输入**

HHHHHHPU

**输出**

1

**输入**

HPUUUHPU

**输出**

2

**source code**

```c
#include <stdio.h>
#include<string.h>
const int N=1e7+1;
int main()
{
    char c[N];
	int t=0;
    gets(c);
	for(int i=2;i<strlen(c);i++){
		if(c[i-2]=='H'&&c[i-1]=='P'&&c[i]=='U')
			t++;
	}
	printf("%d",t);
	return 0;
}
```

## [UVA 1585](https://vjudge.net/problem/UVA-1585/origin)Score

There is an objective test result such as “OOXXOXXOOO”. An ‘O’ means a correct answer of a problem and an ‘X’ means a wrong answer. The score of each problem of this test is calculated by itself and its just previous consecutive ‘O’s only when the answer is correct. For example, the score of the 10th problem is 3 that is obtained by itself and its two previous consecutive ‘O’s. Therefore, the score of “OOXXOXXOOO” is 10 which is calculated by “1+2+0+0+1+0+0+1+2+3”. You are to write a program calculating the scores of test results.

**Input**

Your program is to read from standard input. The input consists of T test cases. The number of test cases T is given in the first line of the input. Each test case starts with a line containing a string composed by ‘O’ and ‘X’ and the length of the string is more than 0 and less than 80. There is no spaces between ‘O’ and ‘X’.

**Output**

Your program is to write to standard output. Print exactly one line for each test case. The line is to contain the score of the test case.

**Sample Input**

```
5 
OOXXOXXOOO 
OOXXOOXXOO 
OXOXOXOXOXOXOX 
OOOOOOOOOO 
OOOOXOOOOXOOOOX
```

**Sample Output**

```
10
9
7
55
30
```

**source code**

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
const int N=1e5+1;
int main()
{
	int n,flag=1,sum=0,t=1;
	char a[N];
	scanf("%d\n",&n);
	while(n--){
		gets(a);
		for(int i=0;i<strlen(a);i++){
			if(a[i]=='X')
				t=0;
			sum+=t;
			t++;
		}
		printf("%d",sum);
	}

	return 0;
}
```

## [UVA 455](https://vjudge.net/problem/UVA-455/origin)Periodic Strings

A character string is said to have period k if it can be formed by concatenating one or more repetitions of another string of length k. For example, the string ”abcabcabcabc” has period 3, since it is formed by 4 repetitions of the string ”abc”. It also has periods 6 (two repetitions of ”abcabc”) and 12 (one repetition of ”abcabcabcabc”). Write a program to read a character string and determine its smallest period.

**Input**

The first line oif the input file will contain a single integer N indicating how many test case that your program will test followed by a blank line. Each test case will contain a single character string of up to 80 non-blank characters. Two consecutive input will separated by a blank line.

**Output**

An integer denoting the smallest period of the input string for each input. Two consecutive output are separated by a blank line.

**Sample Input**

```
1
HoHoHo
```

Sample Output

```
2
```

**source code**

## **A Unique Letter**

**Problem Statement**

You are given a string _S_ of length 3.\
Print a character that occurs only once in _S_.\
If there is no such character, print `-1` instead.

ConstraiConstraints

* _S_ is a string of length 3 consisting of lowercase English letters.

**Input**

Input is given from Standard Input in the following format:

```
S
```

**Output**

Print the answer. If multiple solutions exist, you may print any of them.

**Sample Input 1**

```
pop
```

**Sample Output 1**

```
o
```

`o` occurs only once in `pop`

**Sample Input 2**

```
abc
```

**Sample Output 2**

```
a
```

`a`, `b`, and `c` occur once each in `abc`, so you may print any of them.

**Sample Input 3**

```
xxx
```

**Sample Output 3**

```
-1
```

No character occurs only once in `xxx`.

**source code**

```python
s=input()
for i in set(s):
    if s.count(i)==1:
        print(i)
        break
else:
    print(-1)
```

## [UVA 1586](https://vjudge.net/problem/UVA-1586/origin) Molar mass

```
An organic compound is any member of a large class of chemical compounds whose molecules contain carbon. The molar mass of an organic compound is the mass of one mole of the organic compound. The molar mass of an organic compound can be computed from the standard atomic weights of the elements.

When an organic compound is given as a molecular formula, Dr.CHON wants to find its molar mass. A molecular formula, such as C3H4O3, identifies each constituent element by its chemical symbol and indicates the number of atoms of each element found in each discrete molecule of that compound. If a molecule contains more than one atom of a particular element, this quantity is indicated using a subscript after the chemical symbol. In this problem, we assume that the molecular formula is represented by only four elements, ‘C’ (Carbon), ‘H’ (Hydrogen), ‘O’ (Oxygen), and ‘N’ (Nitrogen) without parentheses. The following table shows that the standard atomic weights for ‘C’, ‘H’, ‘O’, and ‘N’.
```

| Atomic Name            | Carbon      | Hydrogen    | Oxygen      | Nitrogen    |
| ---------------------- | ----------- | ----------- | ----------- | ----------- |
| Standard Atomic Weight | 12.01 g/mol | 1.008 g/mol | 16.00 g/mol | 14.01 g/mol |

For example, the molar mass of a molecular formula C6H5OH is 94.108 g/mol which is computed by 6 × (12.01 g/mol) + 6 × (1.008 g/mol) + 1 × (16.00 g/mol). Given a molecular formula, write a program to compute the molar mass of the formula.

**Input**

Your program is to read from standard input. The input consists of T test cases. The number of test cases T is given in the first line of the input. Each test case is given in a single line, which contains a molecular formula as a string. The chemical symbol is given by a capital letter and the length of the string is greater than 0 and less than 80. The quantity number n which is represented after the chemical symbol would be omitted when the number is 1 (2 ≤ n ≤ 99).

**Output**

Your program is to write to standard output. Print exactly one line for each test case. The line should contain the molar mass of the given molecular formula.

Sample Input

```
4
C
C6H5OH
NH2CH2COOH
C12H22O11
```

**Sample Output**

```
12.010
94.108
75.070
342.296
```

**source code**

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
const int N=1e5;
double f(char a){
   switch(a){
      case 'C':return 12.01;
      case 'H':return 1.008;
      case 'O':return 16.00;
      case 'N':return 14.01;
   }
   return 0;
}
int main()
{
	int i=0,j;
	int n;
   	double sum=0,num=0;
   	char c,h,o,a[N];
   	scanf("%d\n",&n);
   	while(n--){
		scanf("%s",a);
		sum=0;
		int t=strlen(a);
		for(int i=0;i<t;i++){
			if (isdigit(a[i+1]) && isdigit(a[i+2])) 		//判断后两位是不是数字
				num=(a[i+1]-'0')*10+a[i+2]-'0';				//数字存入num
		else 
			if (isdigit(a[i+1])) 							//判断后一位是不是数字
				num=a[i+1]-'0';
		else 
			num=1;											//无数字默认1

			sum+=f(a[i])*num;			//字符*num存入sum
		}
		
		printf("%.3lf\n",sum);
   }
   return 0;
}
```

## [UVA 1225](https://vjudge.net/problem/UVA-1225/origin) Digit Counting

Trung is bored with his mathematics homeworks. He takes a piece of chalk and starts writing a sequence of consecutive integers starting with 1 to N (1 < N < 10000). After that, he counts the number of times each digit (0 to 9) appears in the sequence. For example, with N = 13, the sequence is:

```
12345678910111213
```

In this sequence, 0 appears once, 1 appears 6 times, 2 appears 2 times, 3 appears 3 times, and each digit from 4 to 9 appears once. After playing for a while, Trung gets bored again. He now wants to write a program to do this for him. Your task is to help him with writing this program.

**Input**

The input file consists of several data sets. The first line of the input file contains the number of data sets which is a positive integer and is not bigger than 20. The following lines describe the data sets. For each test case, there is one single line containing the number N.

**Output**

For each test case, write sequentially in one line the number of digit 0, 1, . . . 9 separated by a space.

**Sample Input**

```
2
3
13
```

**Sample Output**

```
0 1 1 1 0 0 0 0 0 0
1 6 2 2 1 1 1 1 1 1
```

**source code**

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
const int N=1e5+1;
int main()
{
	int n,t,i;
	int a[N];
	memset(a,0,sizeof(a));
	scanf("%d\n",&n);
	while(n--){
		scanf("%d",&t);
		for(int i=1;i<=t;i++){
			int num=i;
			while(num){
				a[num%10]++;
				num/=10;
			}
		}

		for(int i=0;i<10;i++){
			printf("%d",a[i]);
				if(i!=9)
					printf(" ");
		}
		printf("\n");
		memset(a,0,sizeof(a));
	}

	return 0;
}
```

## [UVA 10340](https://vjudge.net/problem/UVA-10340/origin) All in All

You have devised a new encryption technique which encodes a message by inserting between its characters randomly generated strings in a clever way. Because of pending patent issues we will not discuss in detail how the strings are generated and inserted into the original message. To validate your method, however, it is necessary to write a program that checks if the message is really encoded in the final string.

Given two strings `s` and `t`, you have to decide whether `s` is a subsequence of `t`, i.e. if you can remove characters from `t` such that the concatenation of the remaining characters is `s`.

**Input**

The input contains several testcases. Each is specified by two strings `s`, `t` of alphanumeric ASCII characters separated by whitespace. Input is terminated by `EOF`.

**Output**

For each test case output, if `s` is a subsequence of `t`.

**Sample Input**

```
sequence subsequence 
person compression 
VERDI vivaVittorioEmanueleReDiItalia 
caseDoesMatter CaseDoesMatter
```

Sample Output

```
Yes
No
Yes
No
```

**source code**

```c
#include<stdio.h>
#include<string.h>
const int N=1e5;
//只要判断s1的元素都在s2里即可
int main()
{
    int i,j,num=0;
    char s1[N],s2[N];
    while(~scanf("%s %s",s1,s2)){
        num=0;
        int t1=strlen(s1),t2=strlen(s2);
        for(i=0;i<t2;i++){              //s1从头遍历，只要s1的一个元素等于s2中的一个元素，则s1+1(num+1) 下一个地址
            if(s1[num]==s2[i])          
                num++;
        }
        if(num==t1)                     
            printf("Yes\n");
        else printf("No\n");
    }
    return 0;
}
```

## CF1703B ICPC Balloons

In an ICPC contest, balloons are distributed as follows:

* Whenever a team solves a problem, that team gets a balloon.
* The first team to solve a problem gets an additional balloon.

A contest has 26 problems, labelled A, B, C, ..., Z. You are given the order of solved problems in the contest, denoted as a string s, where the i-th character indicates that the problem si has been solved by some team. No team will solve the same problem twice.

Determine the total number of balloons that the teams recieved. Note that some problems may be solved by none of the teams.

**Input**

The first line of the input contains an integer t (1≤t≤100) — the number of testcases.

The first line of each test case contains an integer n (1≤n≤50) — the length of the string.

The second line of each test case contains a string ss of length n consisting of uppercase English letters, denoting the order of solved problems.

**Output**

For each test case, output a single integer — the total number of balloons that the teams received.

**Example**

**Input**

```
6
3
ABA
1
A
3
ORZ
5
BAAAA
4
BKPT
10
CODEFORCES
```

**Output**

```
5
2
6
7
8
17
```

**Note**

In the first test case, `5` balloons are given out:

* Problem `A`is solved. That team receives `2` balloons: one because they solved the problem, an an additional one because they are the first team to solve problem `A`.
* Problem `B` is solved. That team receives `2` balloons: one because they solved the problem, an an additional one because they are the first team to solve problem `B`.
* Problem `A` is solved. That team receives only `1` balloon, because they solved the problem. Note that they don't get an additional balloon because they are **not** the first team to solve problem `A`.

The total number of balloons given out is `2+2+1=5`.

In the second test case, there is only one problem solved. The team who solved it receives `2` balloons: one because they solved the problem, an an additional one because they are the first team to solve problem `A`.

**source code**

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<ctype.h>
const int N=1e5;
int main()
{
    int t,n,a[150]={0};
    char c[150],s;
    scanf("%d",&n);
    while(n--){
        scanf("%d\n",&t);
        memset(c,0,sizeof(c));
        int sum=0;
        for(int i=0;i<t;i++){
            s=getchar();
            if(!c[s]){
                c[s]=1;
                sum+=2;
            }
            else sum+=1;
        }
        printf("%d\n",sum);
    }
    return 0;
}
```

## [AtCoder260 ](https://atcoder.jp/contests/abc260/tasks/abc260\_c)**Changing Jewels**

**Problem Statement**

Takahashi has a red jewel of level _N_. (He has no other jewels.)\
Takahashi can do the following operations any number of times.

* Convert a red jewel of level _n_ (_n_ is at least 2) into "a red jewel of level (_n\_−1) and X_ blue jewels of level \_n\*".
* Convert a blue jewel of level _n_ (_n_ is at least 2) into "a red jewel of level (_n\_−1) and Y_ blue jewels of level (\_n\*−1)".

Takahashi wants as many blue jewels of level 1 as possible. At most, how many blue jewels of level 1 can he obtain by the operations?

Input

Input is given from Standard Input in the following format:

```
N X Y
```

**Output**

Print the answer.

**Sample Input 1**

```
2 3 4
```

**Sample Output 1**

```
12
```

Takahashi can obtain 12 blue jewels of level 1 by the following conversions.

* First, he converts a red jewel of level 2 into a red jewel of level 1 and 3 blue jewels of level 2.
  * After this operation, Takahashi has 1 red jewel of level 1 and 3 blue jewels of level 2.
* Next, he repeats the following conversion 3 times: converting a blue jewel of level 2 into a red jewel of level 1 and 4 blue jewels of level 11.
  * After these operations, Takahashi has 4 red jewels of level 1 and 12 blue jewels of level 1.
* He cannot perform a conversion anymore.

He cannot obtain more than 12 blue jewels of level 1, so the answer is 12.

**Sample Input 2**

```
1 5 5
```

**Sample Output 2**

```
0
```

Takahashi may not be able to obtain a blue jewel of level 1.

**Sample Input 3**

```
10 5 5
```

**Sample Output 3**

```
3942349900
```

Note that the answer may not fit into a 32-bit integer type.

**source code**

## [AtCoder](https://atcoder.jp/contests/abc260/tasks/abc260\_a)**A Unique Letter**

**Problem Statement**

You are given a string _S_ of length 3.\
Print a character that occurs only once in S\*.\
If there is no such character, print `-1` instead.

**Constraints**

* _S_ is a string of length 3 consisting of lowercase English letters.

**Input**

Input is given from Standard Input in the following format:

```
S
```

Output

Print the answer. If multiple solutions exist, you may print any of them.

**Sample Input 1**

```
pop
```

**Sample Output 1**

```
o
```

`o` occurs only once in `pop`.

**Sample Input 2**

```
abc
```

**Sample Output 2**

```
a
```

`a`, `b`, and `c` occur once each in `abc`, so you may print any of them.

**Sample Input 3**

```
xxx
```

**Sample Output 3**

```
-1
```

No character occurs only once in `xxx`.

**source code**

```c
#include <stdio.h>

int cnt[27];
char s[7];

int main(){
	scanf("%s", &s[1]);
	for (int i = 1; i <= 3; i++){
		cnt[s[i] - 'a' + 1]++;
	}
	for (int i = 1; i <= 26; i++){
		if (cnt[i] == 1){
			printf("%c", i + 'a' - 1);
			return 0;
		}
	}
	printf("-1");
	return 0;
}
```

## [UVA1339](https://vjudge.net/problem/UVA-1339) 古老的密码

**source code**

```c
#include<stdio.h>
#include<string.h>
//计算字母频率
//字母出现次数存入数组
//排序后让每个元素相等即可	#测试
void bubble(int a[],int n){
    for(int i=0;i<n;i++){
        for(int j=0;j<n-i-1;j++){
            if(a[j]>a[j+1]){
                int t=a[j];
                a[j]=a[j+1];
                a[j+1]=t;
            }
        }
    }
}
int main(){
    char s1[100000],s2[100000];
    int a1[100000]={0},a2[100000]={0};
    while(~scanf("%s %s",s1,s2)){
        memset(a1,0,sizeof(a1));
        memset(a2,0,sizeof(a2));
        int len1=strlen(s1),len2=strlen(s2),cnt=0,flag=1;
        for(int i=0;i<len1;i++){        //存数组
            a1[s1[i]-'A']++;
            a2[s2[i]-'A']++;    
        }

        bubble(a1,26);                //排序
        bubble(a2,26);

        /*for(int i=0;i<26;i++)			//测试
            printf("%d ",a1[i]);
        printf("\n");
        for(int i=0;i<26;i++)
            printf("%d ",a2[i]);
        printf("\n");*/

        for(int i=0;i<26;i++){
            if(a1[i]!=a2[i]){
                flag=0;
                break;
            }
        }
        if(!flag)
            printf("NO\n");
        else printf("YES\n");
    }
    return 0;
}
```

## [UVA489](https://vjudge.net/problem/UVA-489) 刽子手游戏

刽子手游戏其实是一款猜单词游戏,游戏规则是这样的：计算机想一个单词 让你猜，你每次可以猜一个字母。如果单词里有 那个字母，所有该字母会显示出来；如果没有那 个字母，则计算机会在一幅“刽子手”画上填一 笔。这幅画一共需要7笔就能完成，因此你最多只能错6次。注意，猜一个已经猜过的字母也算错。

在本题中，你的任务是编写一个“裁判”程 序，输入单词和玩家的猜测，判断玩家赢了 （You win.）、输了（You lose.）还是放弃了 （You chickened out.）。每组数据包含3行，第1 行是游戏编号（-1为输入结束标记），第2行是 计算机想的单词，第3行是玩家的猜测。后两行保证只含小写字母。

**样例输入：**

```
1
cheese 
chese 
2
cheese 
abcdefg 
3
cheese 
abcdefgij 
-1
```

**样例输出:**

```
Round 1 
You win. 
Round 2 
You chickened out. 
Round 3 
You lose.
```

**source code**

```c
#include <cstdio>
#include<iostream>
#include<bits/stdc++.h>
using namespace std;
int win=0,lose=0,sum=0,temp=0,leave,chance;
char s1[10000],s2[10000];
void guess(char c){
    leave=1;
    for(int i=0;i<strlen(s1);i++){
        if(s1[i]==c){
            temp++;			//相等记1次
            s1[i]=' ';		//把s1中相同的字符都替换成' '，降重
            leave=0;		
        }
    }
    if(temp==strlen(s1))win=1;	//s2所有字符都和s1相等，即s2是s1的子集，win
    if(leave)chance--;			//leave!=0，即s2中有字符不是s1的子集 减一次机会
    if(!chance)lose=1;			//7次机会用完，lose
}
int main()
{
    int n;
    
    while(cin>>n&&(n!=-1)){
        printf("Round %d\n",n);
        win=0,lose=0,sum=0,temp=0;
        cin>>s1>>s2;
        chance=7;		//7次机会
        for(int i=0;i<strlen(s2);i++){
            guess(s2[i]);
            if(win||lose)
                break;
        }
    
        if(win)printf("You win.\n");
        else if(lose)printf("You lose.\n");
        else printf("You chickened out.\n");
    }
    return 0;
}
```

## [HDU4841](https://vjudge.net/problem/HDU-4841/origin) 圆桌问题

圆桌上围坐着2n个人。其中n个人是好人，另外n个人是坏人。如果从第一个人开始数数，数到第m个人，则立即处死该人；然后从被处死的人之后开始数数，再将数到的第m个人处死……依此方法不断处死围坐在圆桌上的人。试问预先应如何安排这些好人与坏人的座位，能使得在处死n个人之后，圆桌上围坐的剩余的n个人全是好人。

**Input**

多组数据，每组数据输入：好人和坏人的人数n（<=32767）、步长m（<=32767）；

**Output**

对于每一组数据，输出2n个大写字母，‘G’表示好人，‘B’表示坏人，50个字母为一行，不允许出现空白字符。相邻数据间留有一空行。

**Sample**

| Input | Output |
| ----- | ------ |
| 2 3   | GBBG   |
| 2 4   | BGGB   |

**source code**

```c
#include<iostream>
#include<vector>
#include<queue>
#include<stack>
using namespace std;
int main(){
    int n,m;
    vector<int>q;
    int x,k=0;
    while(cin >> n >> m){
        q.clear();
        k=0;
        x=0;
        for(int i=0;i<2*n;i++)
            q.push_back(i);
        for(int i=0;i<n;i++){
            x=(x+m-1)%q.size();
            q.erase(q.begin()+x);
        }
        for(int i=0;i<2*n;i++){
            if(i%50==0&&i){
                cout << endl;
            }
            if(k<q.size()&&i==q[k]){
                k++;
                cout<<'G';
            }else cout<<'B';
        }
        cout<<endl<<endl;
    }
    return 0;
}
```

## [HDU1062](https://vjudge.net/problem/HDU-1062/origin) Text Reverse

Ignatius likes to write words in reverse way. Given a single line of text which is written by Ignatius, you should reverse all the words and then output them.

**Input**

The input contains several test cases. The first line of the input is a single integer T which is the number of test cases. T test cases follow.\
Each test case contains a single line with several words. There will be at most 1000 characters in a line.

**Output**

For each test case, you should output the text which is processed.

**Sample**

| Input        | Output       |
| ------------ | ------------ |
| 1            | hello world! |
| olleh !dlrow |              |
|              |              |

**source code**

```c
#include<iostream>
#include<string>
#include<vector>
#include<stack>
#include<algorithm>
using namespace std;
int main(){
	int n;
	char c;
	stack<char>s;
	cin >> n;
	getchar();		//接收'\n'
	while(n--){
		while(1){
			c=getchar();
			if(c==' '||c=='\n'||c==EOF){
				while(!s.empty()){
					cout << s.top();		//返回空格前的栈顶
					s.pop();				//删除栈顶
				}
				if(c=='\n'||c==EOF){
					break;
				}
				cout << ' ';
			}else s.push(c);				//原来都是栈顶...跟数组不一样
		}									//依此压入hello,hello都在栈顶
		cout << endl;
	}
	return 0;
}
```

## [Atcoder BC261](https://atcoder.jp/contests/abc261/tasks/abc261\_a) Intersection

**Problem Statement**

We have a number line. Takahashi painted some parts of this line, as follows:

* First, he painted the part from `X=L_1 to X=R_1`red.
* Next, he painted the part from `X=L_2 to X=R_2`blue.

Find the length of the part of the line painted both red and blue.

**Input**

Input is given from Standard Input in the following format:

```
L_1 R_1 L_2 R_2
```

**Output**

Print the length of the part of the line painted both red and blue, as an integer.

**Sample Input 1**

```
0 3 1 5
```

**Sample Output 1**

```
2
```

The part from `X=0 to X=3` is painted red, and the part from `X=1 to X=5` is painted blue.

Thus, the part from `X=1 to X=3` is painted both red and blue, and its length is `2`.

**source code**

```c
#include<iostream>
#include<algorithm>
using namespace std;
int main(){
	int l1,r1,l2,r2,sum=0;
	cin >> l1 >> r1 >> l2 >> r2;
	for(int i=l1+1;i<=r1;i++){
		for(int j=l2+1;j<=r2;j++){
			if(j==i)
				sum++;
		}
	}
	cout << sum;
	return 0;
}
```

## [Atcoder BC261](https://atcoder.jp/contests/abc261/tasks/abc261\_b) Tournament Result

**Problem Statement**

Nplayers played a round-robin tournament.

You are given an N-by-N table A containing the results of the matches. Let A(i,j) denote the element at the i-th row and j-th column of A.\
A(i,j) is `-` if `i=j`, and `W`, `L`, or `D` otherwise.

A(i,j)is `W` if Player i beat Player j, `L` if Player i lost to Player j, and `D` if Player `i` drew with Player `j`.

Determine whether the given table is contradictory.

The table is said to be contradictory when some of the following holds:

* There is a pair (i,j) such that Player i beat Player j, but Player j did not lose to Player i;
* There is a pair (i,j) such that Player i lost to Player j, but Player j did not beat Player i;
* There is a pair (i,j) such that Player idrew with Player j, but Player j did not draw with Player i.

**Sample Input 1**

```
4
-WWW
L-DD
LD-W
LDW-
```

**Sample Output 1**

```
incorrect
```

Player 3 beat Player 4, while Player 4 also beat Player 3, which is contradictory.

**source code**

```c
#include<stdio.h>
char a[100000][1000];
int main(){
	int n;
    scanf("%d\n",&n);
    for(int i=1;i<=n;i++)
        for(int j=1;j<=n;j++)
            scanf("%c\n",&a[i][j]);
    
    
    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            if(i==j)continue;
            if(a[i][j]=='W'&&a[j][i]!='L'){
                printf("incorrect");
                return 0;
            }
            if(a[i][j]=='L'&&a[j][i]!='W'){
                printf("incorrect");
                return 0;
            }
            if(a[i][j]=='D'&&a[j][i]!='D'){
                printf("incorrect");
                return 0;
            }
        }
    }
    printf("correct");
    return 0;
}
```

## [Atcoder BC261](https://atcoder.jp/contests/abc261/tasks/abc261\_c) NewFolder(1)

**Problem Statement**

For two strings A and B, let A+B denote the concatenation of A and B in this order.

You are given N strings S1,…,SN. Modify and print them as follows, in the order i=1,…, N:

**Sample Input 1**

```
5
newfile
newfile
newfolder
newfile
newfolder
```

**Sample Output 1**

```
newfile
newfile(1)
newfolder
newfile(2)
newfolder(1)
```

**source code**

```c
#include<map>
#include<iostream>
#include<string>
using namespace std;
char s[221000][1000]; 
int main(){	
    map<string,int>count;
    int n;
	scanf("%d\n",&n);
    for(int i=1;i<=n;i++){
		scanf("%s",&s[i]);
		count[s[i]]=0;
	}
    for(int i=1;i<=n;i++){
		count[s[i]]++;
		if(count[s[i]]==1)
			printf("%s\n",s[i]);
		else printf("%s(%d)\n",s[i],count[s[i]]-1);
	}
    return 0;
}
```

## HDU2648 Shopping

Every girl likes shopping,so does dandelion. Now she finds the shop is increasing the price every day because the Spring Festival is coming .She is fond of a shop which is called "memory". Now she wants to know the rank of this shop's price after the change of everyday.

**Input**

One line contains a number n ( n<=10000),stands for the number of shops.\
Then n lines ,each line contains a string (the length is short than 31 and only contains lowercase letters and capital letters.)stands for the name of the shop.\
Then a line contains a number m (1<=m<=50),stands for the days .\
Then m parts , every parts contains n lines , each line contains a number s and a string p ,stands for this day ,the shop p 's price has increased s.

**Output**

Contains m lines ,In the ith line print a number of the shop "memory" 's rank after the ith day. We define the rank as :If there are t shops' price is higher than the "memory" , than its rank is t+1.

**Sample**

**Input**

```
3
memory
kfc
wind
2
49 memory
49 kfc
48 wind
80 kfc
85 wind
83 memory
```

**Output**

```
1
2
```

**source code**

```c
#include<iostream>
#include<algorithm>
#include<string>
#include<map>
using namespace std;
map<string,int>shop;
string s,s1[10000];
int main(){
	int n,m,p,num;
    
    while(cin >> n){
        int t=n;
        for(int i=0;i<n;i++){
            cin >> s1[i];
            shop[s1[i]]=0;
            if(s1[i]=="memory")
                num=i;
        }
        cin >> m;
        while(m--){
            for(int i=1;i<=n;i++){
                cin >> p >> s;
                shop[s]+=p;
            }
            int rank=1;
            for(int i=0;i<n;i++){
                if(shop[s1[i]]>shop[s1[num]])
                    rank++;
            }
            cout << rank << endl;
        }
        shop.clear();
    }

    return 0;
}
```

## Ignatius and the Princess II

**题目**

给定一个从1到N的序列，我们定义1,2,3…N-1,N，是所有可以由1到N组成的序列中最小的序列（每个数字只能使用一次）。 因此，很容易看到第二个最小的序列是1,2,3…N，N-1。 现在我给你两个数字N和M。你应该告诉我第M个最小的序列，它由1到N组成。

输入：每个测试用例均包含两个数字N和M（1 <= N <= 1000，1 <= M <= 10000）。 您可能会假设总是有一个序列满足BEelzebub的需求。 输入在文件末尾终止。

输出：对于每个测试用例，您只需输出满足BEelzebub要求的序列即可。 输出序列时，应在两个数字之间打印一个空格，但不要在最后一个数字之后输出任何空格。

**Input**

```
6 4
11 8
```

**Output**

```
1 2 3 5 6 4
1 2 3 4 5 6 7 9 8 11 10
```

**source code**

```c
#include<iostream>
#include<algorithm>
#include<string>
#include<map>
#include<set>
#include<vector>
using namespace std;
int main(){
	int n,m;
    while(cin >> n >> m){
        vector<int>a(n,0);
        for(int i=0;i<n;i++)
            a[i]=i+1;
        
        int num=0;
        do{
            num++;
            if(num==m){
                for(int i=0;i<n;i++){
                    cout << a[i];
                    if(i!=n-1)
                        cout << ' ';
                }
                cout << '\n';
                break;
            }
        }while(next_permutation(a.begin(),a.end()));
    }
    return 0;
}
```

## [HDU1716](https://acm.hdu.edu.cn/showproblem.php?pid=1716) 排列2

Ray又对数字的列产生了兴趣：\
现有四张卡片，用这四张卡片能排列出很多不同的4位数，要求按从小到大的顺序输出这些4位数。

**Input**

每组数据占一行，代表四张卡片上的数字（0<=数字<=9），如果四张卡片都是0，则输入结束。

**Output**

对每组卡片按从小到大的顺序输出所有能由这四张卡片组成的4位数，千位数字相同的在同一行，同一行中每个四位数间用空格分隔。\
每组输出数据间空一行，最后一组数据后面没有空行。

**Sample**

**Input**

```
1 2 3 4
1 1 2 3
0 1 2 3
0 0 0 0
```

**Output**

```
1234 1243 1324 1342 1423 1432
2134 2143 2314 2341 2413 2431
3124 3142 3214 3241 3412 3421
4123 4132 4213 4231 4312 4321

1123 1132 1213 1231 1312 1321
2113 2131 2311
3112 3121 3211

1023 1032 1203 1230 1302 1320
2013 2031 2103 2130 2301 2310
3012 3021 3102 3120 3201 3210
```

**source code**

```c
#include<iostream>
#include<algorithm>
#include<string>
#include<map>
#include<set>
#include<vector>
#include<stack>
#include<queue>
#include<deque>
using namespace std;
int main(){
	int n,a[10];
    int x=0;
    while(~scanf("%d%d%d%d",&a[0],&a[1],&a[2],&a[3]) && (a[0] || a[1] || a[2] || a[3])){
        sort(a,a+4);				//先排序
        if(x)						//空格分隔
            cout << '\n';
        x=1;
        int f=0,k=0;
        do{
            if(a[0]==0)				
                continue;
                
            if(!k)					//初始k==0，f==0，a[0]还未赋给f
                k=1;
            else 
                if(f!=a[0])			//千位不同则换行
                    cout << '\n';
                else 
                    cout << ' ';	//相同则空格

            for(int i=0;i<4;i++)	
                cout << a[i];		//输出
            f=a[0];					//赋值
        }while(next_permutation(a,a+4));
        cout << '\n';
    }    
    return 0;
}
```

## [UVA-10815](https://vjudge.net/problem/UVA-10815) Andy's First Dictionary

Andy, 8, has a dream - he wants to produce his very own dictionary. This is not an easy task for him, as the number of words that he knows is, well, not quite enough. Instead of thinking up all the words himself, he has a briliant idea. From his bookshelf he would pick one of his favorite story books, from which he would copy out all the distinct words. By arranging the words in alphabetical order, he is done! Of course, it is a really time-consuming job, and this is where a computer program is helpful.

You are asked to write a program that lists all the different words in the input text. In this problem, a word is defined as a consecutive sequence of alphabets, in upper and/or lower case. Words with only one letter are also to be considered. Furthermore, your program must be CaSe InSeNsItIvE. For example, words like "Apple", "apple" or "APPLE" must be considered the same.

**Input**

The input file is a text with no more than 5000 lines. An input line has at most 200 characters. Input is terminated by EOF.

**Output**

Your output should give a list of different words that appears in the input text, one in a line. The words should all be in lower case, sorted in alphabetical order. You can be sure that he number of distinct words in the text does not exceed 5000.

**Input**

```
Adventures in Disneyland
Two blondes were going to Disneyland when they came to a fork in the
road. The sign read: "Disneyland Left."
So they went home.
```

**Output**

```
a
adventures
blondes
came
disneyland
fork
going
home
in
left
read
road
sign
so
the
they
to
two
went
were
when
```

**source code**

```c
#include<iostream>
#include<algorithm>
#include<string>
#include<map>
#include<set>
#include<vector>
#include<stack>
#include<queue>
#include<deque>
using namespace std;
int main(){
	string s,h;
    set<string>ss;
    while(cin >> s){
        for(int i=0;i<s.length();i++)
            if(isalpha(s[i])){		//判断是否字母
                s[i]=tolower(s[i]);	//都换成小写
                h+=s[i];			
            }else 					//如果是符号
                break;				//则break
        if(h.length()){				//把符号前的字符inset到set里
            ss.insert(h);
            h.clear();				//再clear为下次使用
        }
    }
    for(set<string>::iterator it=ss.begin();it!=ss.end();it++)		//迭代器
        cout << *it << endl;
    return 0;
}
```

## N皇后问题

在N\*N的方格棋盘放置了N个皇后，使得它们不相互攻击（即任意2个皇后不允许处在同一排，同一列，也不允许处在与棋盘边框成45角的斜线上。\
你的任务是，对于给定的N，求出有多少种合法的放置方法。

**Input**

共有若干行，每行一个正整数N≤10，表示棋盘和皇后的数量；如果N=0，表示结束。

**Output**

共有若干行，每行一个正整数，表示对应输入行的皇后的不同放置数量。

**Sample**

**Input**

```
1
8
5
0
```

**Output**

```
1
92
10
```

**source code**

```c
#include<iostream>
#include<algorithm>
#include<cstring>
#include<map>
#include<set>
#include<vector>
#include<stack>
#include<queue>
#include<deque>
using namespace std;
int cnt,n;
int a[100],b[100];
//row是行,a[row]是列
bool check(int x,int y){
    for(int i=1;i<x;i++){
        if(a[i]==y)return false;    //判断列
        if(i+a[i]==x+y)return false;    //判断斜线
        if(i-a[i]==x-y)return false;    //判断斜线
    }
    return true;
}
void dfs(int row){
    if(row==n+1){
        cnt++;
        return;
    }
    for(int i=1;i<=n;i++){
        if(check(row,i)){           //判断行列
            a[row]=i;
            dfs(row+1);
        }
    }
}
int main(){
    for(n=0;n<=10;n++){
        memset(a,0,sizeof(a));
        cnt=0;
        dfs(1);
        b[n]=cnt;           //打表，不然超时
    }
	while(cin >> n && n)
        cout << b[n] << endl;
    return 0;
}
```

```c
/*打表*/
#include <iostream> 
#include <stdio.h> 
#include <cstring>
using namespace std; 
int n;
int main() {
while(cin >> n) {
    if(n==0)   
        break;
    if(n==1){
        printf("1\n");
        continue;} 
    if(n==2) {
        printf("0\n");
        continue;} 
    if(n==3) {
        printf("0\n");
        continue;} 
    if(n==4) {
        printf("2\n");
        continue;} 
    if(n==5) {
        printf("10\n");
        continue;} 
    if(n==6) {
        printf("4\n");
        continue;} 
    if(n==7) {
        printf("40\n");
        continue;} 
    if(n==8) {
        printf("92\n");
        continue;} 
    if(n==9) {
        printf("352\n");
        continue;} 
    if(n==10) {
        printf("724\n");
        continue;}
}
	return 0; 
}
```

**additional term**

输出每一种方案，每种方案顺序输出皇后所在的列号，若无方案，则输出no solute!

**source code**

```
#include<iostream>
#include<algorithm>
#include<cstring>
#include<map>
#include<set>
#include<vector>
#include<stack>
#include<queue>
#include<deque>
using namespace std;
int cnt,n,flag=1;
int a[100],b[100];
//row是行,a[row]是列
bool check(int x,int y){
    for(int i=1;i<x;i++){
        if(a[i]==y)return false;    //判断列
        if(i+a[i]==x+y)return false;    //判断斜线
        if(i-a[i]==x-y)return false;    //判断斜线
    }
    return true;
}
void dfs(int row){
    if(row==n+1){
        for(int i=1;i<row;i++){
            printf("%5d",a[i]);
            flag=0;
        }
        printf("\n");
    }
    for(int i=1;i<=n;i++){
        if(check(row,i)){
            a[row]=i;
            dfs(row+1);
        }
        
    }
}
int main(){
	scanf("%d",&n);
    dfs(1);
    if(flag)
        printf("No solute!\n");
    return 0;
}
```

## [HDU1312](https://vjudge.net/problem/HDU-1312/origin) Red and Black

There is a rectangular room, covered with square tiles. Each tile is colored either red or black. A man is standing on a black tile. From a tile, he can move to one of four adjacent tiles. But he can't move on red tiles, he can move only on black tiles.

Write a program to count the number of black tiles which he can reach by repeating the moves described above.

**Input**

The input consists of multiple data sets. A data set starts with a line containing two positive integers W and H; W and H are the numbers of tiles in the x- and y- directions, respectively. W and H are not more than 20.

There are H more lines in the data set, each of which includes W characters. Each character represents the color of a tile as follows.

'.' - a black tile\
'#' - a red tile\
'@' - a man on a black tile(appears exactly once in a data set)

**Output**

For each data set, your program should output a line which contains the number of tiles he can reach from the initial tile (including itself).

**Sample**

**Input**

```
6 9
....#.
.....#
......
......
......
......
......
#@...#
.#..#.
11 9
.#.........
.#.#######.
.#.#.....#.
.#.#.###.#.
.#.#..@#.#.
.#.#####.#.
.#.......#.
.#########.
...........
11 6
..#..#..#..
..#..#..#..
..#..#..###
..#..#..#@.
..#..#..#..
..#..#..#..
7 7
..#.#..
..#.#..
###.###
...@...
###.###
..#.#..
..#.#..
0 0
```

**output**

```
45
59
6
13
```

**source code**

```c
#include<iostream>
#include<queue>
using namespace std;

static char room[23][23];
static int dir[4][2] = {    //往右转90°的数轴
    {-1,0}, //向左
    {0,-1},//向上
    {1,0},//向右
    {0,1}//向下
};
static int Wx,Hy,num;//Wx行，Hy列，用num统计可走的位置有多少

#define CHECK(x,y) (x<Wx && x>=0 && y>=0 && y<Hy)//判断是否在room中

struct node {
    int x;
    int y;
};

void BFS(int dx,int dy)
{
    num=1; //起点也包含在砖块内
    queue<node> q; //队列中放坐标点
    node start,next;
    start.x = dx;
    start.y = dy;
    q.push(start);
    while(!q.empty()){
        start = q.front();
        q.pop();
        for(int i=0;i<4;++i){//按左、上、右、下 4个方向顺时针逐一搜索
            next.x = start.x + dir[i][0];
            next.y = start.y + dir[i][1];
            if(CHECK(next.x,next.y) && room[next.x][next.y] == '.'){
                room[next.x][next.y] = '#'; //进队之后标记为已经处理过
                num++;
                q.push(next);
            }
        }
    }
}

int main()
{
    int x,y,dx(0),dy(0);
    while(cin>>Wx>>Hy){ //Wx行，Hy列
        if(Wx==0 && Hy==0) //结束
            break;
        for(y=0;y<Hy;++y){//有Hy列
            for(x=0;x<Wx;++x){ //一次读入一行
                cin>>room[x][y];
                if(room[x][y] == '@'){ //读入起点
                    dx = x;
                    dy = y;
                }
            }
        }
        num = 0;
        BFS(dx,dy);
        cout<<num<<endl;
    }
    return 0;
}
```

## Leetcode200 Number of Islands

Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return _the number of islands_.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

**Example 2:**

```
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
```

**Constraints:**

* `m == grid.length`
* `n == grid[i].length`
* `1 <= m, n <= 300`
* `grid[i][j]` is `'0'` or `'1'`.

**source code**

```c
//参考https://www.youtube.com/watch?v=XSmgFKe-XYU
/*
 * @lc app=leetcode.cn id=200 lang=cpp
 *
 * [200] 岛屿数量
 */

// @lc code=start
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {	//二维数组
        if(grid.empty())return 0;
        int m = grid.size();	//行
        int n = grid[0].size();	//列
        int ans = 0;
        for(int y = 0; y < m; ++y)
            for(int x = 0; x < n; ++x){
                ans += grid[y][x] - '0';
                dfs(grid, x, y, m, n);
            }
        return ans;
    }
private:
    void dfs(vector<vector<char>>& grid, int x, int y, int m, int n){
        if(x < 0 || y < 0 || x >= n || y >= m || grid[y][x] == '0')
            return ;
        grid[y][x] = '0';
        dfs(grid, x + 1, y, m, n);	//右
        dfs(grid, x - 1, y, m, n);	//左
        dfs(grid, x, y + 1, m, n);	//上
        dfs(grid, x, y - 1, m, n);	//下
    }
};
// @lc code=end
```

## 取余运算

**题目描述**

输入`b`，`p`，`k`的值，求`b^p mod k`的值（即b的p次方除以k的余数）。其中`b`，`p`，`k*k`为32位整数。

**样例输入**

```
2 10 9
```

**样例输出**

```
2^10 mod 9=7
```

**source code**

```c
#include<iostream>
#include<algorithm>
#include<string>
#include<map>
#include<set>
#include<vector>
#include<stack>
#include<queue>
#include<deque>
using namespace std;
int b, p;
long long k;
int f(int p){
    int t;
    if(!p)
        return 1;
    t = f(p / 2) % k;
    t = (t * t) % k;
    if (p % 2 == 1)
        t = (t * b) % k;
    return t;
}
int main(){
    cin >> b >> p >> k;
    int temp = b;
    b %= k;
    printf("%d^%d mod %d=%d\n", temp, p, k, f(p));
    return 0;
}
```

## 剪绳子

**题目描述**

有`N`根绳子，第`i`根绳子长度为`Li`，现在需要`M`根等长的绳子，你可以对`N`根绳子进行任意裁剪（不能拼接），请你帮忙计算出这`M`根绳子最长的长度是多少。

**输入**

第一行包含2个正整数N、M，表示原始绳子的数量和需求绳子的数量。

第二行包含N个整数，其中第 i 个整数Li表示第 i 根绳子的长度。

已知：`1≤N,M≤100000, 0<Li<10^9`

**输出**

输出一个数字，表示裁剪后最长的长度，保留两位小数。

**样例输入**

```
3 4
3 5 4
```

**样例输出**

```
2.50
```

**提示**

第一根和第三根分别裁剪出一根2.50长度的绳子，第二根剪成2根2.50长度的绳子，刚好4根。

**source code**

```c
#include<iostream>
#include<algorithm>
#include<string>
#include<map>
#include<set>
#include<vector>
#include<stack>
#include<queue>
#include<deque>
using namespace std;
const int N = 1e6;
const double eps = 1e-4;
int n, m;
long long L[N];
bool check(double mid){
	long long res = 0;
	for (int i = 0; i < n;i++){
		res += L[i] / mid;
		if(res>=m)
			return true;
	}
	return false;
}
int main(){
	cin >> n >> m;
	for (int i = 0; i < n;i++)
		cin >> L[i];
	double l = 0, r = 1e9;	//一般没给条件的话，区间设为(-∞,+∞),此题
	while (r - l > eps){	//保留k位小数，二分时区间长度<1e(-k^2)即可，此题1e-4即可
		double mid = (l + r) / 2;
		if (check(mid))
			l = mid;
		else
			r = mid;
	}
	printf("%.2lf\n", l);
	return 0;
}
```

## Leetcode704 [二分查找](https://leetcode.cn/problems/binary-search/description/)

给定一个 `n` 个元素有序的（升序）整型数组 `nums` 和一个目标值 `target` ，写一个函数搜索 `nums` 中的 `target`，如果目标值存在返回下标，否则返回 `-1`。

**示例 1:**

```
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
```

**示例 2:**

```
输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1
```

**提示：**

* 你可以假设 `nums` 中的所有元素是不重复的。
* `n` 将在 `[1, 10000]`之间。
* `nums` 的每个元素都将在 `[-9999, 9999]`之间。

**source code**

```c
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l = 0, r = nums.size()-1;
        while(l<=r){
            int mid = (r - l) / 2 + l;
            int num = nums[mid];
            if (num == target)
                return mid;
            else if (num > target)
                r = mid - 1;
            else
                l = mid + 1;
        }
        return -1;
    }
};
```

## [ACwing67](https://www.acwing.com/problem/content/63/) 数字在排序数组中出现的次数

统计一个数字在排序数组中出现的次数。

例如输入排序数组 \[1,2,3,3,3,3,4,5] 和数字 33，由于 33 在这个数组中出现了 44 次，因此输出 44。

**数据范围**

数组长度 \[0,1000]

**样例**

```
输入：[1, 2, 3, 3, 3, 3, 4, 5] ,  3

输出：4
```

**source code**

```c
class Solution
{
public:
    int getNumberOfK(vector<int> &nums, int k)
    {
        if (nums.empty())
            return 0;
        int l = 0, r = nums.size() - 1;
        while (l < r)
        {
            int mid = l + r >> 1;
            if (nums[mid] >= k)
                r = mid;
            else
                l = mid + 1;
        }
        if (nums[l] != k)
            return 0;
        int start = l;
        l = 0, r = nums.size() - 1;
        while (l < r)
        {
            int mid = l + r + 1 >> 1;
            if (nums[mid] <= k)
                l = mid;
            else
                r = mid - 1;
        }
        int end = r;
        if (start == end)
            return end;
        return start - end + 1;
    }
};
```

## [Leetcode231](https://leetcode.cn/problems/power-of-two/description/) 2的幂

给你一个整数 `n`，请你判断该整数是否是 2 的幂次方。如果是，返回 `true` ；否则，返回 `false` 。

如果存在一个整数 `x` 使得 `n == 2x` ，则认为 `n` 是 2 的幂次方。

**示例 1：**

```
输入：n = 1
输出：true
解释：20 = 1
```

**示例 2：**

```
输入：n = 16
输出：true
解释：24 = 16
```

**示例 3：**

```
输入：n = 3
输出：false
```

**示例 4：**

```
输入：n = 4
输出：true
```

**示例 5：**

```
输入：n = 5
输出：false
```

**提示：**

* `-2^31 <= n <= 2^31 - 1`

**source code**

```c
/*
 * @lc app=leetcode.cn id=231 lang=cpp
 *
 * [231] 2 的幂
 */

// @lc code=start
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1)) == 0;
    }
};
// @lc code=end
```

## [ACwing801](https://www.acwing.com/problem/content/803/)  二进制中1的个数

给定一个长度为 `n`的数列，请你求出数列中每个数的二进制表示中 `1`的个数。

**输入格式**

第一行包含整数 `n`

第二行包含 `n`个整数，表示整个数列

**输出格式**

共一行，包含 `n`个整数，其中的第 `i`个数表示数列中的第 `i`个数的二进制表示中 `1`的个数

**数据范围**

`1`≤`n`≤`100000`\
`0`≤`数列中元素的值`≤`10^9`

**输入样例：**

```
5
1 2 3 4 5
```

**输出样例：**

```
1 1 2 1 2
```

**source code**

```c
#include <iostream>
using namespace std;
#define out(x) for(int i=0;i<x;i++)
int main()
{
    int n, t;
    cin >> n;
    out(n)
    {
        int sum = 0;
        cin >> t;
        while (t)
            t &= (t - 1), sum++;
        cout << sum << ' ';
    }
    return 0;
}
```

## [面试题 16.01. ](https://leetcode.cn/problems/swap-numbers-lcci/)交换数字

编写一个函数，不用临时变量，直接交换numbers = \[a, b]中a与b的值。

**示例：**

```
输入: numbers = [1,2]
输出: [2,1]
```

**提示：**

* `numbers.length == 2`
* `-2147483647 <= numbers[i] <= 2147483647`

**source code**

```c
class Solution {
public:
    vector<int> swapNumbers(vector<int>& numbers) {
        int a=numbers[0],b=numbers[1];
        a=a^b;
        b=a^b;
        a=a^b;
        return {a,b};
    }
};
```

## A+B Problem（高精）

**题目描述**

高精度加法，相当于 a+b problem，**不用考虑负数**。

**输入格式**

分两行输入。a,b \leq 10^{500}_a_,\_b\_≤10500。

**输出格式**

输出只有一行，代表 a+b\_a\_+_b_ 的值。

**输入输出样例**

**输入**

```
1
1
```

\*\*输出 \*\*

```
2
```

\*\*输入 \*\*

```
1001
9099
```

**输出**

```
10100
```

**source code**

```c
#include <iostream>
#include <vector>
#define out(x) for (int i = x.size() - 1; i >= 0; i--)
using namespace std;
// 加引用避免再拷贝整个数组
vector<int> add(vector<int> &A, vector<int> &B)
{
    // 定义储存结果的vector以及进位t，第0位没有进位->初始化为0
    vector<int> result;
    int t = 0;
    // 从个位开始遍历直至遍历完A和B的所有位
    for (int i = 0; i < A.size() || i < B.size(); i++)
    {
        // 每一次用t表示Ai，Bi与上一个数的进位这三个数的和
        if (i < A.size())
            t += A[i];
        if (i < B.size())
            t += B[i];
        // 当前这一位输出t除以10的余数
        result.push_back(t % 10);
        // t是否进位
        t /= 10;
    }
    // 如果最高位有进位则补1
    if (t)
        result.push_back(t);
    return result;
}
int main()
{
    // 使用字符串读入
    string a, b;
    vector<int> A, B;
    cin >> a >> b; // a = "123456"
    // 使用vector逆序读入,变成整数需要减去偏移量0
    out(a) A.push_back(a[i] - '0'); // A = [6,5,4,3,2,1]
    out(b) B.push_back(b[i] - '0');
    // 相当于vector<int>
    auto C = add(A, B);
    // 倒序输出
    out(C) cout << C[i];
    return 0;
}
```

python版

```python
a=int(input())
b=int(input())
print(a+b)
```

## [NOIP2015 普及组](https://www.luogu.com.cn/problem/P2670) 扫雷游戏

**题目描述**

扫雷游戏是一款十分经典的单机小游戏。在 ![](https://g.yuque.com/gr/latex?n#card=math\&code=n\&id=GvF7V) 行 ![](https://g.yuque.com/gr/latex?m#card=math\&code=m\&id=zNr3O) 列的雷区中有一些格子含有地雷（称之为地雷格），其他格子不含地雷（称之为非地雷格）。玩家翻开一个非地雷格时，该格将会出现一个数字——提示周围格子中有多少个是地雷格。游戏的目标是在不翻出任何地雷格的条件下，找出所有的非地雷格。

现在给出 ![](https://g.yuque.com/gr/latex?n#card=math\&code=n\&id=wrJD7) 行 ![](https://g.yuque.com/gr/latex?m#card=math\&code=m\&id=mGRGL) 列的雷区中的地雷分布，要求计算出每个非地雷格周围的地雷格数。

注：一个格子的周围格子包括其上、下、左、右、左上、右上、左下、右下八个方向上与之直接相邻的格子。

**输入格式**

第一行是用一个空格隔开的两个整数 ![](https://g.yuque.com/gr/latex?n#card=math\&code=n\&id=fo5bv) 和 ![](https://g.yuque.com/gr/latex?m#card=math\&code=m\&id=VJqPb)，分别表示雷区的行数和列数。

接下来 ![](https://g.yuque.com/gr/latex?n#card=math\&code=n\&id=kMeQY) 行，每行 ![](https://g.yuque.com/gr/latex?m#card=math\&code=m\&id=bVmuH) 个字符，描述了雷区中的地雷分布情况。字符 ![](https://g.yuque.com/gr/latex?%5Ctexttt%7B\*%7D#card=math\&code=%5Ctexttt%7B%2A%7D\&id=OmFQs) 表示相应格子是地雷格，字符 ![](https://g.yuque.com/gr/latex?%5Ctexttt%7B%3F%7D#card=math\&code=%5Ctexttt%7B%3F%7D\&id=U7tkI) 表示相应格子是非地雷格。相邻字符之间无分隔符。

**输出格式**

输出文件包含 ![](https://g.yuque.com/gr/latex?n#card=math\&code=n\&id=HRy4f) 行，每行 ![](https://g.yuque.com/gr/latex?m#card=math\&code=m\&id=aJAZg) 个字符，描述整个雷区。用 ![](https://g.yuque.com/gr/latex?%5Ctexttt%7B\*%7D#card=math\&code=%5Ctexttt%7B%2A%7D\&id=U0Uip) 表示地雷格，用周围的地雷个数表示非地雷格。相邻字符之间无分隔符。

**样例输入**

```
3 3
*??
???
?*?
```

**样例输出**

```
*10
221
1*1
```

**样例输入**

```
2 3
?*?
*??
```

**样例输出**

```
2*1
*21
```

**提示**

对于 ![](https://g.yuque.com/gr/latex?100%5C%25#card=math\&code=100%5C%25\&id=QMBeX)的数据，![](https://g.yuque.com/gr/latex?1%E2%89%A4n%E2%89%A4100%2C%201%E2%89%A4m%E2%89%A4100#card=math\&code=1%E2%89%A4n%E2%89%A4100%2C%201%E2%89%A4m%E2%89%A4100\&id=gHVtx)。

**source code**

```c
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>
#include <set>
#include <map>
#include <cstring>
#define out(v, x) for (int v = 1; v <= x; v++)
using namespace std;
const int N = 1e4;
bool mine[N][N];
int main()
{
    memset(mine, 0, sizeof(mine));
    int n, m;
    cin >> n >> m;
    char c;
    out(i, n) out(j, m){
        cin >> c;
        mine[i][j] = (c == '*');
    }
        out(i, n){
            out(j, m){
                if (mine[i][j]==1)
                    printf("*");
                else
                    printf("%d", mine[i + 1][j - 1] + mine[i + 1][j] + mine[i + 1][j + 1] + mine[i][j - 1] + mine[i][j + 1] + mine[i - 1][j - 1] + mine[i - 1][j] + mine[i - 1][j + 1]);
            }
            printf("\n");
        }
        return 0;
}
```

## [Leetcode74](https://leetcode.cn/problems/search-a-2d-matrix/) 搜索二维矩阵

编写一个高效的算法来判断 `m x n` 矩阵中，是否存在一个目标值。该矩阵具有如下特性：

* 每行中的整数从左到右按升序排列。
* 每行的第一个整数大于前一行的最后一个整数。

**示例 1：**

![](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg#id=odZFw\&originHeight=242\&originWidth=322\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

```
输入：matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
输出：true
```

**示例 2：**

![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/11/25/mat2.jpg#id=hkejZ\&originHeight=242\&originWidth=322\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

```
输入：matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
输出：false
```

**提示：**

* `m == matrix.length`
* `n == matrix[i].length`
* `1 <= m, n <= 100`
* `-104 <= matrix[i][j], target <= 104`

**source code**

```c
/*
 * @lc app=leetcode.cn id=74 lang=cpp
 *
 * [74] 搜索二维矩阵
 */

// @lc code=start
class Solution
{
public:
    bool searchMatrix(vector<vector<int>> &matrix, int target)
    {
        int n = matrix.size(), m = matrix[0].size();
        if (matrix.empty() || matrix[0].empty())
            return 0;
        vector<int> a;
        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++)
                a.push_back(matrix[i][j]);		//把二维matrix存到一维数组

        int l = 0, r = a.size() - 1;
        //二分
        while (l < r)
        {
            int mid = l + r >> 1;
            if (a[mid] >= target)
                r = mid;
            else
                l = mid + 1;
        }
        if(a[r]!=target)
            return 0;
        return 1;
    }
};
// @lc code=end
```

## [Leetcode153](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array/description/) 寻找旋转排序数组中的最小值

已知一个长度为 `n` 的数组，预先按照升序排列，经由 `1` 到 `n` 次 **旋转** 后，得到输入数组。例如，原数组 `nums = [0,1,2,4,5,6,7]` 在变化后可能得到：

* 若旋转 `4` 次，则可以得到 `[4,5,6,7,0,1,2]`
* 若旋转 `7` 次，则可以得到 `[0,1,2,4,5,6,7]`

注意，数组 `[a[0], a[1], a[2], ..., a[n-1]]` **旋转一次** 的结果为数组 `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]` 。

给你一个元素值 **互不相同** 的数组 `nums` ，它原来是一个升序排列的数组，并按上述情形进行了多次旋转。请你找出并返回数组中的 **最小元素** 。

你必须设计一个时间复杂度为 `O(log n)` 的算法解决此问题。

**示例 1：**

```
输入：nums = [3,4,5,1,2]
输出：1
解释：原数组为 [1,2,3,4,5] ，旋转 3 次得到输入数组。
```

**示例 2：**

```
输入：nums = [4,5,6,7,0,1,2]
输出：0
解释：原数组为 [0,1,2,4,5,6,7] ，旋转 4 次得到输入数组。
```

**示例 3：**

```
输入：nums = [11,13,15,17]
输出：11
解释：原数组为 [11,13,15,17] ，旋转 4 次得到输入数组。
```

**提示：**

* `n == nums.length`
* `1 <= n <= 5000`
* `-5000 <= nums[i] <= 5000`
* `nums` 中的所有整数 **互不相同**
* `nums` 原来是一个升序排序的数组，并进行了 `1` 至 `n` 次旋转

**source code**

```c
/*
 * @lc app=leetcode.cn id=153 lang=cpp
 *
 * [153] 寻找旋转排序数组中的最小值
 */

// @lc code=start
class Solution {
public:
    int findMin(vector<int>& nums) {
        int l = 0, r = nums.size();
        while(l<r){
            int mid = l + r >> 1;
            if(nums[mid]<=nums.back())
                r = mid;
            else
                l = mid + 1;
        }
        return nums[r];
    }
};
// @lc code=end
```

![](https://assets.leetcode-cn.com/solution-static/153/1.png#id=L80mc\&originHeight=913\&originWidth=2000\&originalType=binary\&ratio=1\&rotation=0\&showTitle=false\&status=done\&style=none\&title=)

## [Leetcode33](https://leetcode.cn/problems/search-in-rotated-sorted-array/description/) 搜索旋转排序数组

整数数组 `nums` 按升序排列，数组中的值 **互不相同** 。

在传递给函数之前，`nums` 在预先未知的某个下标 `k`（`0 <= k < nums.length`）上进行了 **旋转**，使数组变为 `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]`（下标 **从 0 开始** 计数）。例如， `[0,1,2,4,5,6,7]` 在下标 `3` 处经旋转后可能变为 `[4,5,6,7,0,1,2]` 。

给你 **旋转后** 的数组 `nums` 和一个整数 `target` ，如果 `nums` 中存在这个目标值 `target` ，则返回它的下标，否则返回 `-1` 。

你必须设计一个时间复杂度为 `O(log n)` 的算法解决此问题。

**示例 1：**

```
输入：nums = [4,5,6,7,0,1,2], target = 0
输出：4
```

**示例 2：**

```
输入：nums = [4,5,6,7,0,1,2], target = 3
输出：-1
```

**示例 3：**

```
输入：nums = [1], target = 0
输出：-1
```

**提示：**

* `1 <= nums.length <= 5000`
* `-104 <= nums[i] <= 104`
* `nums` 中的每个值都 **独一无二**
* 题目数据保证 `nums` 在预先未知的某个下标上进行了旋转
* `-104 <= target <= 104`

**source code**

```c
/*
 * @lc app=leetcode.cn id=33 lang=cpp
 *
 * [33] 搜索旋转排序数组
 */

// @lc code=start
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(nums.empty())
            return -1;
        int l = 0, r = nums.size() - 1;
        while(l < r){
            int mid = l + (r - l) / 2;
            if(nums[mid] <= nums.back())
                r = mid;
            else
                l = mid + 1;
        }
        if(target <= nums.back())
            r = nums.size() - 1;
        else
            l = 0, r--;
        while(l < r){
            int mid = l + (r - l) / 2;
            if(nums[mid] >= target)
                r = mid;
            else
                l = mid + 1;
        }
        if(nums[l]==target)
            return l;
        return -1;
    }
};
// @lc code=end
```
