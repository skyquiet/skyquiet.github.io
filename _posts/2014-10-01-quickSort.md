---
title:  "Quick Sort"
date:   2014-10-01 22:00:00
categories: arithmetic
---

**快速排序**

* 快速排序使用**分治法**来设计算法。
* 拆分是快速排序的核心。
* 快速排序的最坏运行时间是**O(n2)**，但期望的运行时间是**O(nlgn)**。



**图形表示**
![快速排序](http://pic002.cnblogs.com/images/2012/401709/2012090309575126.png)

**Code Java**

{% highlight java %}

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
            while (low < high && data[high] >= tmp) {
                high--;
            }
            //出现右边的值不小于tmp的时候进行互换
            data[low] = data[high];
            //然后从左边继续挨个比较，保持左边的值比tmp小，否则跳出循环
            while (low < high && data[low] <= tmp) {
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

**Code PHP**

{% highlight PHP %}

<?php

/**
 * Created by IntelliJ IDEA.
 * User: Sun
 * Date: 2015/11/12
 * Time: 16:12
 */
class MySort
{
    /**
     * 先来个快速排序
     * @param $arr
     * @param $Start
     * @param $end
     * @return mixed
     */
    public static function quickSort(&$arr, $start, $end)
    {
        echo "---->".$start."--->".$end.""\n<br>"";
        if (empty($arr) || $start > $end) {
            return;
        }
        $t = self::part($arr, $start, $end);
        self::quickSort($arr, $start, $t - 1);
        self::quickSort($arr, $start + 1, $end);
    }
    public static function part(&$arr, $low, $high)
    {
        $tmp = $arr[$low];
        while ($low < $high) {
            while ($low < $high && $tmp <= $arr[$high]) {
                $high--;
            }
            //swap
            $arr[$low] = $arr[$high];
            while ($low < $high && $tmp >= $arr[$low]) {
                $low++;
            }
            $arr[$high] = $arr[$low];
        }
        $arr[$low] = $tmp;
        return $low;
    }
}

echo "start ---------------->";
$arr = array(2, 77, 334, 4,2, 5, 6);

MySort::quickSort($arr, 0, count($arr)-1);
var_dump($arr);

{% endhighlight %}
