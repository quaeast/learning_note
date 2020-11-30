# loop invariant，循环不变式

循环不变式是证明算法中非常常见的一个概念。这个概念从正向理解，可以套用维基百科

> In computer science, a loop invariant is a property of a program loop that is true before (and after) each iteration. It is a logical assertion, sometimes checked within the code by an assertion call. Knowing its invariant(s) is essential in understanding the effect of a loop.

> 在计算机科学领域，一个循环不变式是程序循环的一个性质。它在每一次迭代之前（和之后）都是正确的。它是一个逻辑断言，有时候在代码中被显示地检查。判断他一致的正确性是理解循环效果的关键。

定义太枯燥，用《算法导论》中的插入排序的实际例子来理解，下面是插入排序的 java 实现：

```java
public static void insertSort(int[] array) {
        for (int i = 1; i < array.length; i++) {
            int key = array[i];
            int j = i - 1;
            while (j >= 0 && array[j] >= key) {
                array[j + 1] = array[j];
                j--;
            }
            array[j + 1] = key;
        }
    }
```

按照定义，我们可以找到很多在循环中一直正确的断言，但是既然这是一个排序算法，我们就找一个对我没来讲有意义的断言：

**`array[0 : i+1]` （按照 Python 切片，左闭右开，下同）是升序的，并且其中的元素都是 `array[1 : i]` 原本的元素。**

那么问题来了，这个断言有什么用呢？可以从三个角度去审视这个证明，从而证明算法的正确性。引用算法导论的原文：

> Initialization: It is true prior to the first iteration of the loop.
> Maintenance: If it is true before an iteration of the loop, it remains true before the
next iteration.
> Termination: When the loop terminates, the invariant gives us a useful property that helps show that the algorithm is correct.

首先是初始化的时候，这个断言显然是正确的。

之后是状态的维持，在每次循环之前和之后，都是一个被插入好的升序序列，并且新来的元素原本在末尾，也属于 `array[0 : i+1]`。

最后，在循环结束的时候，可以看到，`array[0 : i+1]` 是一个升序数组，他所有的元素都正好属于原来的数组。算法正确。