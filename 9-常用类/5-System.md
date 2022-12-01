# System

```java
public class Main {
    public static void main(String[] args) {
        // exit:
        // status 0: 正常状态
        System.exit(0);

        // arrayCopy
        int[] arr1 = {1, 2, 3};
        int[] arr2 = new int[3]; // {0, 0, 0}
        System.arraycopy(arr1, 0, arr2, 0, 3);

        // currentTimeMillens
        long ctm = System.currentTimeMillis();
        System.out.println(ctm);

        // gc
        System.gc();
    }
}
```

