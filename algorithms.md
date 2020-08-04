# 算法

![](/Users/hedongwei/Library/Application Support/typora-user-images/image-20200804124106485.png)

## 	选择排序

### 		代码

~~~java
 public static void sort(int[] arr){
        for (int i = 0; i < arr.length; i++) {
            int minPosition = i;
            // 主要的时间复杂度地方
            for (int j = i + 1; j < arr.length; j++) {
                minPosition = arr[j] < arr[minPosition] ? j : minPosition;
            }
            swap(arr, i, minPosition);
        }
    }

 	/**
     * 交换值
     *
     * @param arr    数组
     * @param source 源值
     * @param target 目标最小值
     */
    public static void swap(int[] arr, int source, int target) {
        int temp = arr[source];
        arr[source] = arr[target];
        arr[target] = temp;
    }

    /**
     * 输出函数
     *
     * @param arr 入参
     */
    private static void print(int[] arr) {
        for (int attr : arr) {
            System.out.print(attr + ",");
        }
        System.out.println();
    }
~~~



### 		代码分析

$$
时间复杂度O(n^2)
$$

### 		思考

​		不稳定的排序算法，如何用程序证明该算法不稳定



## 	冒泡排序

### 		代码

~~~java
/**
     * 冒泡排序
     *
     * @param arr 数组
     */
    public static void sort(int[] arr) {
        for (int i = arr.length - 1; i > 0; i--) {
            findMax(arr, i);
        }
    }

    /**
     * 找到最大的数
     *
     * @param arr 数组
     * @param i   下标
     */
    private static void findMax(int[] arr, int i) {
        for (int j = 0; j < i; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr, j);
            }
        }
    }

    /**
     * 交换数值
     *
     * @param arr 数组
     * @param j   下标
     */
    private static void swap(int[] arr, int j) {
        int temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
    }
~~~



### 		代码分析

$$
时间复杂度O(n^2)
$$

### 		思考

​			该算法最好时间复杂度仍然为O(n^2)，如何改进？

## 插入排序

### 代码

### 代码分析

### 思考

## 归并排序

### 代码

~~~java
public class MergeSort {
    public static void main(String[] args) {
        int arr[] = {1, 4, 6, 3, 6, 8, 9};
        sort(arr, 0, arr.length - 1);
        print(arr);
    }

    //递归过程
    public static void sort(int[] arr, int left, int right) {
        if (left == right)
            return;
        int mid = left + (right - left) / 2;
        //对左边排序
        sort(arr, left, mid);
        //对右边排序
        sort(arr, mid + 1, right);
        //排序归并
        merge(arr, left, right, mid+1);
    }

    //排序归并
    public static void merge(int[] arr, int left, int right, int mid) {
        if (left == right)
            return;
        int i = left;
        int j = mid + 1;
        int k = 0;
        int[] temp = new int[right - left + 1];
        while (i <= mid && j <= right ) {
            temp[k++] = arr[i] <= arr[j] ? arr[i++] : arr[j++];
        }
        while ( j <=right)temp[k++] = arr[j++];
        while (i <= mid) temp[k++] = arr[i++];
        for (int t = 0; t < temp.length; t++) {
            arr[left + t] = temp[t];
        }
    }

}
~~~



### 代码分析

时间复杂度:

​	因为每次会对半分开进行归并排序，每次的时间复杂度是N，次数为logN
$$
时间复杂度：O（Nlog_2N）
$$
空间复杂度:

​	因为每次排序都会分配空间用于临时数组，但是同一时间最多只会分配一个数组
$$
空间复杂度：O(N)
$$
使用场景：

​	java和python对于对象的排序都是使用归并排序

java对象排序：

​	对象排序一般要求稳定，java对象排序使用的实际是TimSort（改进的归并排序，归并和二分插入排序）

### 思考

​	TimSort查看源码

## 快速排序

### 代码

~~~java

public class QuickSort {
    public static void main(String[] args) {
        int[] arr = {0, 6, 2, 5, 7, 10, 5, 6, 9, 2, 10};
        sort(arr, 0, arr.length - 1);
        print(arr);
    }

    //进行排序算法
    public static void sort(int[] arr, int left, int right) {
        if (left >= right) return;
        //得到标杆位置
        int flag = parition(arr, left, right);
        //左排序
        sort(arr, left, flag - 1);
        //右排序
        sort(arr, flag + 1, right);
    }

    /**
     * @param arr   数组
     * @param left  左边界
     * @param right 右边界
     * @return 返回中轴值
     */
    public static int parition(int[] arr, int left, int right) {
        int i = left;
        int j = right - 1;
        while (i <= j) {
            while (i <= j && arr[i] <= arr[right]) i++;
            while (i <= j && arr[j] > arr[right]) j--;
            if (i < j) swap(arr, i, j);

        }
        swap(arr, i, right);
        return i;
    }
}

~~~



### 代码分析

时间复杂度
$$
时间复杂度：O(Nlog_2N)\\
最差时间复杂度：O(N^2)\\
$$
空间复杂度
$$
空间复杂度:O(log_2N)
$$


### 思考

双轴快排？



## 计数排序

### 代码分析

适用场景：

​	数据比较小

​	计数排序是非比较排序

​	适用于特定问题，对元数据有要求

​	空间复杂度N+K，时间复杂度N

### 思考

0～100方便，100～200怎么做映射



