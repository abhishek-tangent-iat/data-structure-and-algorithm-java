# data-structure-and-algorithm-java
dsa(java) : 25 dsa problems to understand array




Count Even and Odd Numbers:
Count the number of even and odd numbers in an array of integers.
java
Copy code
public class EvenOddCount {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int evenCount = 0, oddCount = 0;
        for (int num : arr) {
            if (num % 2 == 0)
                evenCount++;
            else
                oddCount++;
        }
        System.out.println("Even numbers: " + evenCount);
        System.out.println("Odd numbers: " + oddCount);
    }
}
Find Largest and Smallest Elements:
Find the largest and smallest elements in an array of integers.
java
Copy code
public class LargestSmallest {
    public static void main(String[] args) {
        int[] arr = {5, 2, 9, 1, 7, 3};
        int max = arr[0], min = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > max)
                max = arr[i];
            else if (arr[i] < min)
                min = arr[i];
        }
        System.out.println("Largest element: " + max);
        System.out.println("Smallest element: " + min);
    }
}
Find Sum of Even Numbers:
Calculate the sum of all even numbers in an array of integers.
java
Copy code
public class SumOfEven {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int sum = 0;
        for (int num : arr) {
            if (num % 2 == 0)
                sum += num;
        }
        System.out.println("Sum of even numbers: " + sum);
    }
}
Remove Duplicate Elements:
Remove duplicate elements from an array of integers.
java
Copy code
import java.util.Arrays;

public class RemoveDuplicates {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 2, 4, 5, 4, 6};
        Arrays.sort(arr);
        int j = 0;
        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] != arr[i + 1])
                arr[j++] = arr[i];
        }
        arr[j++] = arr[arr.length - 1];
        int[] result = Arrays.copyOf(arr, j);
        System.out.println("Array after removing duplicates: " + Arrays.toString(result));
    }
}
Find Missing Number in Array:
Find the missing number in a consecutive sequence of numbers in an array.
java
Copy code
public class MissingNumber {
    public static void main(String[] args) {
        int[] arr = {1, 2, 4, 5, 6};
        int n = arr.length + 1;
        int totalSum = n * (n + 1) / 2;
        int sum = 0;
        for (int num : arr) {
            sum += num;
        }
        int missingNumber = totalSum - sum;
        System.out.println("Missing number: " + missingNumber);
    }
}
Check for Majority Element:
Check if there exists a majority element (occurs more than n/2 times) in an array.
java
Copy code
public class MajorityElement {
    public static void main(String[] args) {
        int[] arr = {2, 2, 2, 3, 4, 2, 2};
        int count = 0, candidate = 0;
        for (int num : arr) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }
        count = 0;
        for (int num : arr) {
            if (num == candidate)
                count++;
        }
        if (count > arr.length / 2)
            System.out.println("Majority element: " + candidate);
        else
            System.out.println("No majority element");
    }
}
Find Leaders in Array:
Find all the leaders in an array (elements which are greater than all elements to their right).
java
Copy code
public class LeadersInArray {
    public static void main(String[] args) {
        int[] arr = {16, 17, 4, 3, 5, 2};
        int maxFromRight = arr[arr.length - 1];
        System.out.println("Leaders in the array:");
        System.out.print(maxFromRight + " ");
        for (int i = arr.length - 2; i >= 0; i--) {
            if (arr[i] > maxFromRight) {
                maxFromRight = arr[i];
                System.out.print(maxFromRight + " ");
            }
        }
    }
}
Find Frequency of Elements:
Find the frequency of each element in an array.
java
Copy code
import java.util.HashMap;
import java.util.Map;

public class ElementFrequency {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 2, 3, 1, 2, 4};
        Map<Integer, Integer> frequencyMap = new HashMap<>();
        for (int num : arr) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }
        System.out.println("Element frequencies:");
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            System.out.println(entry.getKey() + " occurs " + entry.getValue() + " times");
        }
    }
}
Sort 0s, 1s, and 2s (Dutch National Flag Problem):
Sort an array of 0s, 1s, and 2s in linear time.
java
Copy code
public class Sort012 {
    public static void main(String[] args) {
        int[] arr = {0, 1, 2, 1, 0, 2, 1, 0};
        int low = 0, mid = 0, high = arr.length - 1;
        while (mid <= high) {
            if (arr[mid] == 0) {
                swap(arr, low, mid);
                low++;
                mid++;
            } else if (arr[mid] == 1) {
                mid++;
            } else {
                swap(arr, mid, high);
                high--;
            }
        }
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
Find Peak Element:
Find a peak element in an array (an element which is greater than or equal to its neighbors).
java
Copy code
public class PeakElement {
    public static void main(String[] args) {
        int[] arr = {1, 3, 20, 4, 1, 0};
        int peak = findPeak(arr);
        System.out.println("Peak element: " + peak);
    }

    private static int findPeak(int[] arr) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if ((mid == 0 || arr[mid] >= arr[mid - 1]) && (mid == arr.length - 1 || arr[mid] >= arr[mid + 1]))
                return arr[mid];
            else if (mid > 0 && arr[mid - 1] > arr[mid])
                high = mid - 1;
            else
                low = mid + 1;
        }
        return -1;
    }
}



These programs cover a variety of array-related concepts and algorithms in Java, helping you learn arrays thoroughly from basic to intermediate levels.








Sure! Below are 25 basic to intermediate level Java programs involving arrays, along with explanations:

    Array Declaration and Initialization:

java

public class ArrayDeclaration {
    public static void main(String[] args) {
        // Declaration and initialization of an array
        int[] numbers = {1, 2, 3, 4, 5};
        // Printing array elements
        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }
    }
}

    Array Sum:

java

public class ArraySum {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        int sum = 0;
        // Calculating sum of array elements
        for (int i = 0; i < numbers.length; i++) {
            sum += numbers[i];
        }
        System.out.println("Sum: " + sum);
    }
}

    Array Average:

java

public class ArrayAverage {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        double average;
        int sum = 0;
        // Calculating sum of array elements
        for (int i = 0; i < numbers.length; i++) {
            sum += numbers[i];
        }
        // Calculating average
        average = (double) sum / numbers.length;
        System.out.println("Average: " + average);
    }
}

    Find Maximum Element in Array:

java

public class MaxElement {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 6, 4, 5};
        int max = numbers[0];
        // Finding maximum element in array
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] > max) {
                max = numbers[i];
            }
        }
        System.out.println("Max: " + max);
    }
}

    Find Minimum Element in Array:

java

public class MinElement {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 0, 4, 5};
        int min = numbers[0];
        // Finding minimum element in array
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] < min) {
                min = numbers[i];
            }
        }
        System.out.println("Min: " + min);
    }
}

    Reverse an Array:

java

public class ReverseArray {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        int[] reversed = new int[numbers.length];
        // Reversing the array
        for (int i = 0; i < numbers.length; i++) {
            reversed[numbers.length - 1 - i] = numbers[i];
        }
        // Printing reversed array
        for (int i = 0; i < reversed.length; i++) {
            System.out.println(reversed[i]);
        }
    }
}

    Check if Array is Sorted:

java

public class CheckSorted {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        boolean sorted = true;
        // Checking if array is sorted
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] < numbers[i - 1]) {
                sorted = false;
                break;
            }
        }
        System.out.println("Sorted: " + sorted);
    }
}

    Count Occurrences of an Element:

java

public class CountOccurrences {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 4, 5, 4};
        int target = 4;
        int count = 0;
        // Counting occurrences of an element
        for (int i = 0; i < numbers.length; i++) {
            if (numbers[i] == target) {
                count++;
            }
        }
        System.out.println("Occurrences of " + target + ": " + count);
    }
}

    Merge Two Arrays:

java

public class MergeArrays {
    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3};
        int[] arr2 = {4, 5, 6};
        int[] merged = new int[arr1.length + arr2.length];
        // Merging two arrays
        for (int i = 0; i < arr1.length; i++) {
            merged[i] = arr1[i];
        }
        for (int i = 0; i < arr2.length; i++) {
            merged[arr1.length + i] = arr2[i];
        }
        // Printing merged array
        for (int i = 0; i < merged.length; i++) {
            System.out.println(merged[i]);
        }
    }
}

    Remove Element from Array:

java

import java.util.Arrays;

public class RemoveElement {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        int elementToRemove = 3;
        // Using ArrayList for dynamic size or array
        int[] newArray = new int[numbers.length - 1];
        int index = 0;
        for (int i = 0; i < numbers.length; i++) {
            if (numbers[i] != elementToRemove) {
                newArray[index++] = numbers[i];
            }
        }
        // Printing the new array
        System.out.println(Arrays.toString(newArray));
    }
}



Find Equilibrium Index:
Find an equilibrium index in an array where the sum of elements to the left is equal to the sum of elements to the right.
java
Copy code
public class EquilibriumIndex {
    public static void main(String[] args) {
        int[] arr = {-7, 1, 5, 2, -4, 3, 0};
        int equilibriumIndex = findEquilibriumIndex(arr);
        System.out.println("Equilibrium index: " + equilibriumIndex);
    }

    private static int findEquilibriumIndex(int[] arr) {
        int totalSum = 0, leftSum = 0;
        for (int num : arr) {
            totalSum += num;
        }
        for (int i = 0; i < arr.length; i++) {
            totalSum -= arr[i];
            if (leftSum == totalSum)
                return i;
            leftSum += arr[i];
        }
        return -1;
    }
}
Find Subarray with Given Sum:
Find if there exists a subarray with a given sum in an array of non-negative integers.
java
Copy code
public class SubarrayWithGivenSum {
    public static void main(String[] args) {
        int[] arr = {1, 4, 20, 3, 10, 5};
        int targetSum = 33;
        findSubarrayWithSum(arr, targetSum);
    }

    private static void findSubarrayWithSum(int[] arr, int targetSum) {
        int currentSum = arr[0], start = 0;
        for (int i = 1; i <= arr.length; i++) {
            while (currentSum > targetSum && start < i - 1) {
                currentSum -= arr[start];
                start++;
            }
            if (currentSum == targetSum) {
                System.out.println("Subarray found between indexes " + start + " and " + (i - 1));
                return;
            }
            if (i < arr.length)
                currentSum += arr[i];
        }
        System.out.println("No subarray found with the given sum");
    }
}
Find Maximum Circular Sum Subarray:
Find the maximum sum of a circular subarray (circular means the subarray wraps around to the beginning if needed).
java
Copy code
public class MaximumCircularSum {
    public static void main(String[] args) {
        int[] arr = {8, -4, 3, -5, 4};
        int maxCircularSum = findMaxCircularSum(arr);
        System.out.println("Maximum circular sum: " + maxCircularSum);
    }

    private static int findMaxCircularSum(int[] arr) {
        int maxNormalSum = kadane(arr);
        if (maxNormalSum < 0)
            return maxNormalSum;
        int totalSum = 0;
        for (int num : arr) {
            totalSum += num;
        }
        for (int i = 0; i < arr.length; i++) {
            arr[i] = -arr[i];
        }
        int maxWrapSum = totalSum + kadane(arr);
        return Math.max(maxNormalSum, maxWrapSum);
    }

    private static int kadane(int[] arr) {
        int maxSum = arr[0], currentMax = arr[0];
        for (int i = 1; i < arr.length; i++) {
            currentMax = Math.max(arr[i], currentMax + arr[i]);
            maxSum = Math.max(maxSum, currentMax);
        }
        return maxSum;
    }
}
Find Maximum Length Bitonic Subarray:
Find the maximum length bitonic subarray in an array (bitonic means elements are first in increasing order and then in decreasing order).
java
Copy code
public class MaxLengthBitonicSubarray {
    public static void main(String[] args) {
        int[] arr = {12, 4, 78, 90, 45, 23};
        int maxLength = maxLengthBitonicSubarray(arr);
        System.out.println("Maximum length of bitonic subarray: " + maxLength);
    }

    private static int maxLengthBitonicSubarray(int[] arr) {
        int n = arr.length;
        int[] inc = new int[n];
        int[] dec = new int[n];
        inc[0] = 1;
        dec[n - 1] = 1;
        for (int i = 1; i < n; i++) {
            inc[i] = (arr[i] > arr[i - 1]) ? inc[i - 1] + 1 : 1;
        }
        for (int i = n - 2; i >= 0; i--) {
            dec[i] = (arr[i] > arr[i + 1]) ? dec[i + 1] + 1 : 1;
        }
        int maxLen = 1;
        for (int i = 0; i < n; i++) {
            maxLen = Math.max(maxLen, inc[i] + dec[i] - 1);
        }
        return maxLen;
    }
}
Find Maximum Product Subarray:
Find the contiguous subarray with the largest product in an array of integers.
java
Copy code
public class MaxProductSubarray {
    public static void main(String[] args) {
        int[] arr = {2, 3, -2, 4};
        int maxProduct = maxProductSubarray(arr);
        System.out.println("Maximum product subarray: " + maxProduct);
    }

    private static int maxProductSubarray(int[] arr) {
        int maxProduct = arr[0];
        int maxEndingHere = arr[0];
        int minEndingHere = arr[0];
        for (int i = 1; i < arr.length; i++) {
            int tempMax = maxEndingHere;
            maxEndingHere = Math.max(arr[i], Math.max(arr[i] * maxEndingHere, arr[i] * minEndingHere));
            minEndingHere = Math.min(arr[i], Math.min(arr[i] * tempMax, arr[i] * minEndingHere));
            maxProduct = Math.max(maxProduct, maxEndingHere);
        }
        return maxProduct;
    }
}
Find Triplet with Given Sum:
Find if there exists a triplet in an array with a given sum.
java
Copy code
import java.util.Arrays;

public class TripletWithGivenSum {
    public static void main(String[] args) {
        int[] arr = {1, 4, 45, 6, 10, 8};
        int targetSum = 22;
        boolean tripletExists = findTripletWithSum(arr, targetSum);
        System.out.println("Triplet with given sum exists: " + tripletExists);
    }

    private static boolean findTripletWithSum(int[] arr, int targetSum) {
        Arrays.sort(arr);
        for (int i = 0; i < arr.length - 2; i++) {
            int left = i + 1, right = arr.length - 1;
            while (left < right) {
                int currentSum = arr[i] + arr[left] + arr[right];
                if (currentSum == targetSum)
                    return true;
                else if (currentSum < targetSum)
                    left++;
                else
                    right--;
            }
        }
        return false;
    }
}
Merge Overlapping Intervals:
Merge overlapping intervals in an array of intervals.
java
Copy code
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

public class MergeOverlappingIntervals {
    public static void main(String[] args) {
        int[][] intervals = {{1, 3}, {2, 6}, {8, 10}, {15, 18}};
        int[][] mergedIntervals = merge(intervals);
        System.out.println("Merged intervals: " + Arrays.deepToString(mergedIntervals));
    }

    private static int[][] merge(int[][] intervals) {
        if (intervals == null || intervals.length == 0)
            return new int[0][];
        Arrays.sort(intervals, Comparator.comparingInt(a -> a[0]));
        List<int[]> merged = new ArrayList<>();
        int[] currentInterval = intervals[0];
        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] <= currentInterval[1]) {
                currentInterval[1] = Math.max(currentInterval[1], intervals[i][1]);
            } else {
                merged.add(currentInterval);
                currentInterval = intervals[i];
            }
        }
        merged.add(currentInterval);
        return merged.toArray(new int[merged.size()][]);
    }
}
Find K Closest Elements to a Given Value:
Find the K closest elements to a given value in a sorted array.
java
Copy code
import java.util.ArrayList;
import java.util.List;

public class KClosestElements {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int target = 3, k = 4;
        List<Integer> result = findKClosestElements(arr, target, k);
        System.out.println("K closest elements: " + result);
    }

    private static List<Integer> findKClosestElements(int[] arr, int target, int k) {
        int left = 0, right = arr.length - 1;
        while (right - left + 1 > k) {
            if (Math.abs(arr[left] - target) > Math.abs(arr[right] - target))
                left++;
            else
                right--;
        }
        List<Integer> result = new ArrayList<>();
        for (int i = left; i <= right; i++) {
            result.add(arr[i]);
        }
        return result;
    }
}
Sort an Array of 0s, 1s, and 2s (Dutch National Flag Problem Variant):
Sort an array of 0s, 1s, and 2s without using extra space or sorting algorithms.
java
Copy code
public class Sort012Variant {
    public static void main(String[] args) {
        int[] arr = {0, 1, 1, 0, 2, 2, 0, 1, 2, 0};
        sort012(arr);
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }

    private static void sort012(int[] arr) {
        int low = 0, mid = 0, high = arr.length - 1;
        while (mid <= high) {
            if (arr[mid] == 0) {
                swap(arr, low, mid);
                low++;
                mid++;
            } else if (arr[mid] == 1) {
                mid++;
            } else {
                swap(arr, mid, high);
                high--;
            }
        }
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
Find Longest Consecutive Sequence:
Find the length of the longest consecutive sequence in an unsorted array.
java
Copy code
import java.util.HashSet;
import java.util.Set;

public class LongestConsecutiveSequence {
    public static void main(String[] args) {
        int[] arr = {100, 4, 200, 1, 3, 2};
        int maxLength = longestConsecutive(arr);
        System.out.println("Length of longest consecutive sequence: " + maxLength);
    }

    private static int longestConsecutive(int[] arr) {
        Set<Integer> set = new HashSet<>();
        for (int num : arr) {
            set.add(num);
        }
        int maxLength = 0;
        for (int num : arr) {
            if (!set.contains(num - 1)) {
                int currentNum = num;
                int currentLength = 1;
                while (set.contains(currentNum + 1)) {
                    currentNum++;
                    currentLength++;
                }
                maxLength = Math.max(maxLength, currentLength);
            }
        }
        return maxLength;
    }
}
Find Maximum Product of Two Integers in Array:
Find the maximum product of two integers in an array of positive integers.
java
Copy code
public class MaxProductOfTwoIntegers {
    public static void main(String[] args) {
        int[] arr = {10, 3, 5, 6, 20};
        int maxProduct = maxProductOfTwo(arr);
        System.out.println("Maximum product of two integers: " + maxProduct);
    }

    private static int maxProductOfTwo(int[] arr) {
        int max1 = Integer.MIN_VALUE, max2 = Integer.MIN_VALUE;
        int min1 = Integer.MAX_VALUE, min2 = Integer.MAX_VALUE;
        for (int num : arr) {
            if (num > max1) {
                max2 = max1;
                max1 = num;
            } else if (num > max2) {
                max2 = num;
            }
            if (num < min1) {
                min2 = min1;
                min1 = num;
            } else if (num < min2) {
                min2 = num;
            }
        }
        return Math.max(max1 * max2, min1 * min2);
    }
}
Find Maximum Length of Subarray with Sum Divisible by K:
Find the maximum length of a subarray with a sum divisible by K.
java
Copy code
import java.util.HashMap;
import java.util.Map;

public class MaxLengthSubarraySumDivisibleByK {
    public static void main(String[] args) {
        int[] arr = {4, 5, 0, -2, -3, 1};
        int k = 5;
        int maxLength = maxLengthSubarraySumDivisibleByK(arr, k);
        System.out.println("Maximum length of subarray with sum divisible by K: " + maxLength);
    }

    private static int maxLengthSubarraySumDivisibleByK(int[] arr, int k) {
        Map<Integer, Integer> remainderToIndex = new HashMap<>();
        int maxLength = 0, currentSum = 0;
        remainderToIndex.put(0, -1);
        for (int i = 0; i < arr.length; i++) {
            currentSum += arr[i];
            int remainder = (currentSum % k + k) % k;
            if (remainderToIndex.containsKey(remainder)) {
                maxLength = Math.max(maxLength, i - remainderToIndex.get(remainder));
            } else {
                remainderToIndex.put(remainder, i);
            }
        }
        return maxLength;
    }
}
Sort an Array of 0s, 1s, and 2s (Dutch National Flag Problem Three-way Partitioning):
Sort an array of 0s, 1s, and 2s using three-way partitioning.
java
Copy code
public class Sort012ThreeWayPartition {
    public static void main(String[] args) {
        int[] arr = {0, 1, 1, 2, 0, 1, 2, 2, 0};
        sort012(arr);
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }

    private static void sort012(int[] arr) {
        int low = 0, mid = 0, high = arr.length - 1;
        while (mid <= high) {
            if (arr[mid] == 0) {
                swap(arr, low, mid);
                low++;
                mid++;
            } else if (arr[mid] == 1) {
                mid++;
            } else {
                swap(arr, mid, high);
                high--;
            }
        }
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
Find Duplicate Element in Array:
Find a duplicate element in an array containing n+1 integers where each integer is between 1 and n (inclusive).
java
Copy code
public class DuplicateElement {
    public static void main(String[] args) {
        int[] arr = {1, 3, 4, 2, 2};
        int duplicate = findDuplicate(arr);
        System.out.println("Duplicate element: " + duplicate);
    }

    private static int findDuplicate(int[] arr) {
        int slow = arr[0], fast = arr[arr[0]];
        while (slow != fast) {
            slow = arr[slow];
            fast = arr[arr[fast]];
        }
        fast = 0;
        while (slow != fast) {
            slow = arr[slow];
            fast = arr[fast];
        }
        return slow;
    }
}
Find All Triplets with Zero Sum:
Find all unique triplets in an array that sum up to zero.
java
Copy code
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class TripletsWithZeroSum {
    public static void main(String[] args) {
        int[] arr = {-1, 0, 1, 2, -1, -4};
        List<List<Integer>> triplets = findTripletsWithZeroSum(arr);
        System.out.println("Triplets with zero sum: " + triplets);
    }

    private static List<List<Integer>> findTripletsWithZeroSum(int[] arr) {
        Arrays.sort(arr);
        List<List<Integer>> result = new ArrayList<>();
        for (int i = 0; i < arr.length - 2; i++) {
            if (i == 0 || (i > 0 && arr[i] != arr[i - 1])) {
                int low = i + 1, high = arr.length - 1, sum = -arr[i];
                while (low < high) {
                    if (arr[low] + arr[high] == sum) {
                        result.add(Arrays.asList(arr[i], arr[low], arr[high]));
                        while (low < high && arr[low] == arr[low + 1])
                            low++;
                        while (low < high && arr[high] == arr[high - 1])
                            high--;
                        low++;
                        high--;
                    } else if (arr[low] + arr[high] < sum)
                        low++;
                    else
                        high--;
                }
            }
        }
        return result;
    }
}
Find Minimum Platform Required for Trains:
Find the minimum number of platforms required for a railway station given the arrival and departure times of trains.
java
Copy code
import java.util.Arrays;

public class MinPlatforms {
    public static void main(String[] args) {
        int[] arrival = {900, 940, 950, 1100, 1500, 1800};
        int[] departure = {910, 1200, 1120, 1130, 1900, 2000};
        int minPlatforms = findMinPlatforms(arrival, departure);
        System.out.println("Minimum platforms required: " + minPlatforms);
    }

    private static int findMinPlatforms(int[] arrival, int[] departure) {
        Arrays.sort(arrival);
        Arrays.sort(departure);
        int platforms = 1, minPlatforms = 1;
        int i = 1, j = 0;
        while (i < arrival.length && j < departure.length) {
            if (arrival[i] <= departure[j]) {
                platforms++;
                i++;
                minPlatforms = Math.max(platforms, minPlatforms);
            } else {
                platforms--;
                j++;
            }
        }
        return minPlatforms;
    }
}
Sort an Array of 0s, 1s, and 2s (Counting Sort Variant):
Sort an array of 0s, 1s, and 2s using Counting Sort algorithm.
java
Copy code
public class Sort012CountingSort {
    public static void main(String[] args) {
        int[] arr = {0, 1, 1, 0, 2, 2, 0, 1, 2, 0};
        sort012(arr);
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }

    private static void sort012(int[] arr) {
        int[] count = new int[3];
        for (int num : arr) {
            count[num]++;
        }
        int index = 0;
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < count[i]; j++) {
                arr[index++] = i;
            }
        }
    }
}
Find Maximum Product Subarray with Negative Product Allowed:
Find the maximum product of a subarray in an array of integers where negative product is also allowed.
java
Copy code
public class MaxProductSubarrayWithNegativeProduct {
    public static void main(String[] args) {
        int[] arr = {6, -3, -10, 0, 2};
        int maxProduct = maxProductSubarrayWithNegative(arr);
        System.out.println("Maximum product of subarray with negative product: " + maxProduct);
    }

    private static int maxProductSubarrayWithNegative(int[] arr) {
        int maxProduct = arr[0], minProduct = arr[0], result = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < 0) {
                int temp = maxProduct;
                maxProduct = minProduct;
                minProduct = temp;
            }
            maxProduct = Math.max(arr[i], maxProduct * arr[i]);
            minProduct = Math.min(arr[i], minProduct * arr[i]);
            result = Math.max(result, maxProduct);
        }
        return result;
    }
}
Find Pair with Given Difference:
Find if there exists a pair in an array with a given difference.
java
Copy code
import java.util.HashSet;
import java.util.Set;

public class PairWithGivenDifference {
    public static void main(String[] args) {
        int[] arr = {5, 20, 3, 2, 50, 80};
        int difference = 78;
        boolean pairExists = findPairWithDifference(arr, difference);
        System.out.println("Pair with given difference exists: " + pairExists);
    }

    private static boolean findPairWithDifference(int[] arr, int difference) {
        Set<Integer> set = new HashSet<>();
        for (int num : arr) {
            if (set.contains(num - difference) || set.contains(num + difference))
                return true;
            set.add(num);
        }
        return false;
    }
}
Rearrange Positive and Negative Numbers:
Rearrange positive and negative numbers in an array such that positive and negative numbers are placed alternatively.
java
Copy code
import java.util.Arrays;

public class RearrangePositiveNegative {
    public static void main(String[] args) {
        int[] arr = {-1, 2, -3, 4, 5, 6, -7, 8, 9};
        rearrangePositiveNegative(arr);
        System.out.println("Rearranged array: " + Arrays.toString(arr));
    }

    private static void rearrangePositiveNegative(int[] arr) {
        int pivot = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < 0) {
                swap(arr, i, pivot);
                pivot++;
            }
        }
        int pos = 1, neg = 0;
        while (pos < arr.length && neg < pivot) {
            swap(arr, pos, neg);
            pos += 2;
            neg++;
        }
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
