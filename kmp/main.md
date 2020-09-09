# KMP算法

## 概念

kmp 用于实现子串匹配，可以用来高效地实现 Strstr(String haystack, String needle)，时间复杂度为线性的 O(m+n)。

## 思路和实现

实现 kmp 需要两个部分，首先需要获取 needle 字符串的同首子字符串的相同前后缀的最大长度表，即 pmt （Partial Match Table）。时间复杂度为 O(m)。之后借助 pmt 进行匹配，时间复杂度为 O(m+n)。

其实两个步骤的思路是相同的，第一步相当于 neddle 自己与自己进行匹配。第二步相当于 haystack 和 needle 进行匹配。

## 代码实现

为了便于理解原理，我没有用第一位是 -1 的 next 数组来简化代码，因为那个需要再拐一个弯。

```java
class Solution {
    private static List<Integer> get_pmt(String son) {
        ArrayList<Integer> pmt = new ArrayList<>();
        pmt.add(0);
        int i = 1;
        int j = 0;
        while (i < son.length()) {
            if (son.charAt(i) != son.charAt(j)) {
                if (j == 0) {
                    pmt.add(j);
                    i++;
                } else {
                    j = pmt.get(j-1);
                }
            } else {
                i++;
                j++;
                pmt.add(j);
            }
        }
        return pmt;
    }

    public int strStr(String haystack, String needle) {
        List<Integer> pmt = get_pmt(needle);
        int i = 0;
        int j = 0;
        while (i < haystack.length() && j < needle.length()) {
            if (haystack.charAt(i) != needle.charAt(j)) {
                if (j != 0) {
                    j = pmt.get(j - 1);
                    i--;
                }
            } else {
                j++;
            }
            i++;
        }
        if (j == needle.length()) {
            return i - j;
        } else {
            return -1;
        }
    }
}
```