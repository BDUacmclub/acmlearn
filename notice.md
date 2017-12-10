Q:这个在线裁判系统使用什么样的编译器和编译选项?

A:系统运行于Debian/Ubuntu

	Linux. 使用GNU GCC/G++ 作为C/C++编译器,

	Free Pascal 作为pascal 编译器 ，用

	openjdk-7 编译 Java. 对应的编译选项如下:

  语言   	参数                                      
  C++: 	g++ -fno-asm -Wall -lm --static -std=c++11 -DONLINE_JUDGE -o Main Main.cc
  C:   	gcc Main.c -o Main  -fno-asm -O2 -Wall -lm --static -std=c99 -DONLINE_JUDGE
  Java:	javac -J-Xms32m -J-Xmx256m Main.java        *Java has 2 more seconds and 512M more memory when running and judging.

  编译器版本为（系统可能升级编译器版本，这里仅供参考）:

  gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3)

  glibc 2.19

openjdk 1.7.0_151

---

Q:程序怎样取得输入、进行输出?

A:你的程序应该从标准输入 stdin('Standard 

Input')获取输入，并将结果输出到标准输出 stdout('Standard Output').例如,在C语言可以使用 'scanf' 

，在C++可以使用'cin' 进行输入；在C使用 'printf' ，在C++使用'cout'进行输出.

用户程序不允许直接读写文件, 如果这样做可能会判为运行时错误 "Runtime Error"。题目描述

你的任务是计算a+b。这是为了acm初学者专门设计的题目。你肯定发现还有其他题目跟这道题的标题类似，这些问题也都是专门为初学者提供的。

输入

输入包含一系列的a和b对，通过空格隔开。一对a和b占一行。

输出

对于输入的每对a和b，你需要依次输出a、b的和。

如对于输入中的第二对a和b，在输出中它们的和应该也在第二行。

样例输入

    1 5
    10 20

样例输出

    6
    30



 C++:

    #include <iostream>
    using namespace std;
    int main(){
        int a,b;
        while(cin >> a >> b)
            cout << a+b << endl;
    	return 0;
    }
    

 C:

    #include <stdio.h>
    int main(){
        int a,b;
        while(scanf("%d %d",&a, &b) != EOF)
            printf("%d\n",a+b);
    	return 0;
    }
    

java:

    import java.util.*;
    public class Main{
    	public static void main(String args[]){
    		Scanner cin = new Scanner(System.in);
    		int a, b;
    		while (cin.hasNext()){
    			a = cin.nextInt(); b = cin.nextInt();
    			System.out.println(a + b);
    		}
    	}
    }

---

Q:为什么我的程序在自己的电脑上正常编译，而系统告诉我编译错误!

A:GCC的编译标准与VC6有些不同，更加符合c/c++标准:

- main 函数必须返回int, void main 的函数声明会报编译错误。
- i 在循环外失去定义 "for(int i=0...){...}"
- itoa 不是ansi标准函数.
- __int64 不是ANSI标准定义，只能在VC使用, 但是可以使用long long声明64位整数。
  如果用了int64,试试提交前加一句#define int64 long long, scanf和printf 请使用%lld作为格式，大部分系统是这样不排除例外（比如东秦oj支持__int128）

---

Q:系统返回信息都是什么意思?

A:详见下述:

Pending : 系统忙，你的答案在排队等待. 

Pending Rejudge: 因为数据更新或其他原因，系统将重新判你的答案.

Compiling : 正在编译.

Running & Judging: 正在运行和判断.

Accepted : 程序通过!

  Presentation Error : 答案基本正确，但是格式不对。

  Wrong Answer : 答案不对，仅仅通过样例数据的测试并不一定是正确答案，一定还有你没想到的地方.

  Time Limit Exceeded : 运行超出时间限制，检查下是否有死循环，或者应该有更快的计算方法。

  Memory Limit Exceeded : 超出内存限制，数据可能需要压缩，检查内存是否有泄露。

  Output Limit Exceeded: 输出超过限制，你的输出比正确答案长了两倍.

  Runtime Error : 运行时错误，非法的内存访问，数组越界，指针漂移，调用禁用的系统函数。请点击后获得详细输出。

  Compile Error : 编译错误，请点击后获得编译器的详细输出。


