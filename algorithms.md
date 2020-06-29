# 算法

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