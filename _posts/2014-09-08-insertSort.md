---
title:  "Insert Sort"
date:   2014-09-08 20:37:00
categories: arithmetic
---

插入排序就是每一步都将一个待排数据按其大小插入到已经排序的数据中的适当位置，直到全部插入完毕。


**Code**

{% highlight java %}

/**
 * 插入排序
 * @param data
 */
public static void insertSort(int data[]) {
   int length = data.length;
   int value, i, j;
   for (i = 1; i < length; i++) {
       value = data[i];
       j = i - 1;
       while (j >= 0 && value < data[j]) {
           data[j + 1] = data[j];
           j--;
       }
       data[j + 1] = value;
   }
   print(data);
}

public static void print(int[] data) {
    for (int i = 0; i < data.length; i++) {
        System.out.print(data[i] + "\t");
    }
    System.out.println();
}

{% endhighlight %}
