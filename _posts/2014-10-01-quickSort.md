---
title:  "快速排序"
date:   2014-10-01 22:00:00
categories: arithmetic
---

**快速排序**

* 快速排序使用`分治法`来设计算法。
* 拆分是快速排序的核心。
* 快速排序的最坏运行时间是O(n2)，但期望的运行时间是O(nlgn)。

**Code**

{% highlight java %}

import org.junit.Test;

/**
 * 快速排序
 * Created by Sun on 2014/10/01.
 */
public class Sort {
    public static void main(String[] args) {
        int[] array = {8, 5, 6, 7, 9, 12, 11, 23, 44, 66};
        QuickSort(array, 0, 9);
        print(array);
    }
    /**
     * 快速排序
     * @param data
     * @param low
     * @param high
     */
    public static void QuickSort(int[] data, int low, int high) {
        if (low < high) {
            int pivot = partition(data, low, high);
            QuickSort(data, low, pivot - 1);
            QuickSort(data, pivot + 1, high);
        }
    }
    /**
     * 获取中间的值的位置
     * @param data
     * @param low
     * @param high
     * @return
     */
    public static int partition(int[] data, int low, int high) {
        int tmp = data[low];
        while (low < high) {
            //右边的值比tmp大
            while (low < high && data[high] > tmp) {
                high--;
            }
            //出现右边的值不小于tmp的时候进行互换
            data[low] = data[high];
            //然后从左边继续挨个比较，保持左边的值比tmp小，否则跳出循环
            while (low < high && data[low] < tmp) {
                low++;
            }
            //执行到这里意味着出现左边的值比tmp大，进行互换
            data[high] = data[low];
            //如果tmp还有没与全部的值比较一遍，则low < high ，进入下一次循环
        }
        //全部比较一遍之后，其实low == high，把tmp填入此中间位置
        data[low] = tmp;
        return low;
    }
    /**
     * 打印数字数组
     *
     * @param data
     */
    public static void print(int[] data) {
        for (int i = 0; i < data.length; i++) {
            System.out.print(data[i] + "  ");
        }
        System.out.println("");
    }
}

{% endhighlight %}
