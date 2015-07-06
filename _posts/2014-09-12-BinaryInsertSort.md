---
title:  "Binary Insert Sort"
date:   2014-09-12 21:20:00
categories: arithmetic
---

二分插入排序是在直接插入排序基础上的改良。


**Code**

{% highlight java %}

   /**
     * 二分插入是在直接插入排序基础上的改良
     * 因为当前位置前面的数据都是有序的，所以直接比较前面数据的中间位置的值，能减少比较次数，提升性能
     * @param data
     */
   public static void binaryInsertSort(int[] data) {
        for (int i = 1; i < data.length; i++) {
            if (data[i] < data[i - 1]) {
                // 缓存i处的元素值
                int tmp = data[i];
                // 记录搜索范围的左边界
                int low = 0;
                // 记录搜索范围的右边界
                int high = i - 1;
                while (low <= high) {
                    // 记录中间位置
                    int mid = (low + high) / 2;
                    // 比较中间位置数据和i处数据大小，以缩小搜索范围
                    if (data[mid] < tmp) {
                        low = mid + 1;
                    } else {
                        high = mid - 1;
                    }
                }
                //将low~i处数据整体向后移动1位
                for (int j = i; j > low; j--) {
                    data[j] = data[j - 1];
                }
                data[low] = tmp;
                print(data);
            }
        }
   }

public static void print(int[] data) {
    for (int i = 0; i < data.length; i++) {
        System.out.print(data[i] + "\t");
    }
    System.out.println();
}

{% endhighlight %}
