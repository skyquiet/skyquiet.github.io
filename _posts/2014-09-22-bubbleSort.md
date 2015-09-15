---
title:  "Bubble Sort"
date:   2014-09-22 21:05:00
categories: arithmetic
---

冒泡排序（Bubble Sort）是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。


**冒泡排序算法的步骤**

1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。
3. 针对所有的元素重复以上的步骤，除了最后一个。
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

**图形表示**

![冒泡排序](http://upload.wikimedia.org/wikipedia/commons/3/37/Bubble_sort_animation.gif)

**Code**

{% highlight java %}
/**
 * 冒泡排序
 * 1.一共需要n-1次外循环
 * 2.相邻的两个值比较大小，大的往后换
 */
@Test
public void bubble() {
    int[] data = {2, 34, 54, 4, 36, 4, 66, 3, 2342, 54, 53, 5634, 645, 64, 56, 456, 4564, 564, 564, 564, 564, 564, 564, 5, 234, 76, 56, 6, 7867, 86429875};
    int length = data.length;
    for (int i = 1; i < length; i++) {
        for (int j = 0; j < length - i; j++) {
            if (data[j] > data[j + 1]) {
                //swap
                int tmp = data[j];
                data[j] = data[j + 1];
                data[j + 1] = tmp;
            }
        }
    }
    print(data);
}

/**
 * 反向的冒泡排序，小的往前放
 */
@Test
public void dive() {
    int[] data = {2, 34, 54, 4, 36, 4, 66, 3};
    int length = data.length;
    for (int i = 1; i < length; i++) {
        for (int j = length - i; j > 0; j--) {
            if (data[j - 1] > data[j]) {
                int tmp = data[j - 1];
                data[j - 1] = data[j];
                data[j] = tmp;
            }
        }
    }
    print(data);
}

{% endhighlight %}
