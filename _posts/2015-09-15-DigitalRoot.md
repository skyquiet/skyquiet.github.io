---
title:  "Digital Root"
date:   2015-09-15 11:42:00
categories: arithmetic
---

**Basic**

在刷LeetCode的时候遇到一道关于Digital Root 的题。在wiki上看了Digital Root 的相关资料，现在用自己的话翻译、总结一下。


**介绍**


Digital Root  就是一个非负整数，把它的不同位的值相加，得到的结果再继续相加，重复这个操作，直到结果为个位数。

举例来说，65,536 的 digital root 为7，因为  6 + 5 + 5 + 3 + 6 = 25 , 2 + 5 = 7.

Digital roots 可以根据周期性的规律来计算出结果，这样能避免使用常规的循环、递归等来计算结果，用做算法的话，能节省大量时间，提高性能。

Digital root  有时候也用来做检验和。


**题目**


给定一个非负的int型整数，然后不断的把它不同的位上的数字相加，直到最后的结果为个位数。


**举例**


给定的数字为38，过程如下：
3+8=11，
1+1=2
结果为2.


**注意**


**不能使用循环、递归，算法的时间复杂度需要为O(1).**


*提示*


1. 所有可能的结果，会是什么？
2. 这些结果，是有规律的，还是随机的？
3. 看看wiki的这个文章：[Digital root](https://en.wikipedia.org/wiki/Digital_root#Congruence_formula)


**Code**

{% highlight java %}
package LeetCode;

/**
 * Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.
 * <p/>
 * For example:
 * <p/>
 * Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.
 * <p/>
 * Follow up:
 * Could you do it without any loop/recursion in O(1) runtime?
 * <p/>
 * Hint:
 * <p/>
 * A naive implementation of the above process is trivial. Could you come up with other methods?
 * What are all the possible results?
 * How do they occur, periodically or randomly?
 * You may find this Wikipedia article useful.
 * Created by Sun on 2015/9/14.
 */
public class AddDigits {

public static void main(String[] args) {

//        addDigits(58967867);


for (int i = 0; i <100 ; i++) {
   int res =  addDigits2(i);
    System.out.print(" "+res);
}


//        System.out.println(addDigits(1000));


}

/**
 * 把数字转成字符串，再分割
 * @param num
 * @return
 */
public static int addDigits(int num) {

//判断边界值

String str = Integer.toString(num);
System.out.println(str);

String s[] = str.split("");

int r = 0;

//i从1开始，是因为 0会是""
for (int i = 1; i < s.length; i++) {
    System.out.println(Integer.parseInt(s[i]));
    r += Integer.parseInt(s[i]);
}


if (r >= 10) {
    addDigits(r);
}
System.out.println("end : " + r);
return r;

}

/**
 * 略微好看点咯
 * @param num
 * @return
 */

public static int addDigits2(int num) {

if (num >= 0 && num <= 9) {
    return num;
}

int sum = 0;
while (num > 0) {
    sum += num % 10;
    num = num / 10;
}

return addDigits2(sum);
}

/**
 * 然后发现有digital roots 这种东西
 * @param num
 * @return
 * @see <a href="https://en.wikipedia.org/wiki/Digital_root#Congruence_formula">digital roots </a>
 */
public static int addDigits3(int num) {
    return 1 + (num - 1) % 1;
}

}

{% endhighlight %}
