# array1M

```
import java.util.Arrays;

public class ClosestValueSearch {

    public static void main(String[] args) {
        int[] sampleArray = new int[1000001];
        for (int i = 0; i <= 1000000; i++) {
            sampleArray[i] = i;
        }

        int target = 900001;
        //System.out.println("Array: " + Arrays.toString(sampleArray));
        System.out.println("Target: " + target);

        try {
            int closestValue = findClosest(sampleArray, target);
            System.out.println("ค่าที่ใกล้เคียงที่สุดที่พบ: " + closestValue);

        } catch (IllegalArgumentException e) {
            System.err.println("error: " + e.getMessage());
        }

    }

    public static int findClosest(int[] arr, int target) {

        int low = 0;
        int high = arr.length - 1;

        if (target <= arr[low]) {
            return arr[low];
        }
        if (target >= arr[high]) {
            return arr[high];
        }

        while (low <= high) {

            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                return arr[mid]; // เจอค่าที่ตรงกันพอดี
            } else if (arr[mid] < target) {
                low = mid + 1; // ค้นหาต่อในฝั่งขวา
            } else { // arr[mid] > target
                high = mid - 1; // ค้นหาต่อในฝั่งซ้าย
            }
        }

        long diffLow = Math.abs((long)arr[low] - target);
        long diffHigh = Math.abs((long)arr[high] - target);

        if (diffLow < diffHigh) {
            return arr[low];
        } else {
            return arr[high];
        }
    }

}
```
