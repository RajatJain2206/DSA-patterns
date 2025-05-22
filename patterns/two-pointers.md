# Two Pointers

#Concept
The Two Pointers pattern involves using two indices (or pointers) to iterate through data structures (usually arrays or linked lists) from different directions or at different speeds. It helps reduce time complexity in problems that require searching or comparing elements.

#When to use
- Sorted arrays or linked lists
- Finding pairs or triplets with a target sum
- Palindrome checks
- Removing duplicates in-place
- Reversing arrays or linked lists
- Merging or comparing two sorted arrays

#Example Problems
 Two Sum II - Leetcode 167

Valid Palindrome - Leetcode 125

 Squares of a Sorted Array - Leetcode 977

 Remove Duplicates from Sorted Array - Leetcode 26

 #Template

 Two Sum 

 // Example: Finding a pair with a given target sum in a sorted array

#include <vector>
#include <iostream>
using namespace std;

pair<int, int> twoSumSorted(const vector<int>& arr, int target) {
    int left = 0;
    int right = arr.size() - 1;

    while (left < right) {
        int sum = arr[left] + arr[right];

        if (sum == target) {
            return {left, right}; // Found the pair
        } else if (sum < target) {
            left++; // Need a larger sum
        } else {
            right--; // Need a smaller sum
        }
    }

    return {-1, -1}; // No valid pair found
}

int main() {
    vector<int> arr = {2, 4, 7, 11, 15};
    int target = 9;
    auto result = twoSumSorted(arr, target);

    if (result.first != -1) {
        cout << "Pair found at indices: " << result.first << " and " << result.second << endl;
    } else {
        cout << "No valid pair found." << endl;
    }

    return 0;
}


# Common mistakes
Make sure the array is sorted before using Two Pointers (unless the problem defines the pointer use in another way).

Carefully manage increment/decrement of pointers to avoid infinite loops or skipping valid values.

Use a while loop for flexibility in movement of both pointers.
