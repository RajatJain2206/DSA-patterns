# Two Pointers

# Concept
The Two Pointers pattern involves using two indices (or pointers) to iterate through data structures (usually arrays or linked lists) from different directions or at different speeds. It helps reduce time complexity in problems that require searching or comparing elements.

# When to use
- Sorted arrays or linked lists
- Finding pairs or triplets with a target sum
- Palindrome checks
- Removing duplicates in-place
- Reversing arrays or linked lists
- Merging or comparing two sorted arrays

# Example Problems
 Two Sum II - Leetcode 167

Valid Palindrome - Leetcode 125

 Squares of a Sorted Array - Leetcode 977

 Remove Duplicates from Sorted Array - Leetcode 26

 # Template

 Two Sum 

 // Example: Finding a pair with a given target sum in a sorted array
```cpp
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

```
# Common mistakes
Make sure the array is sorted before using Two Pointers (unless the problem defines the pointer use in another way).

Carefully manage increment/decrement of pointers to avoid infinite loops or skipping valid values.

Use a while loop for flexibility in movement of both pointers.








# Floyd's Tortoise and Hare algorithm
Floyd's Tortoise and Hare algorithm, also known as Floyd's Cycle Detection algorithm, is an algorithm used to detect loops (cycles) in data structures like linked lists or arrays. It has been proven to reliably detect cycles under specific circumstances and can be applied to finding duplicate elements.

This algorithm employs two pointers, referred to as the "tortoise" and the "hare," to traverse the list.

Tortoise: A pointer that advances one step at a time through the list.

Hare: A pointer that advances two steps at a time through the list.
Using these pointers, you progress until the hare catches up with the tortoise or a cycle is detected.

# Here's an overview of the algorithm:

Phase 1 (Cycle Detection):
Move the tortoise and hare, advancing the hare twice as fast as the tortoise, until the hare catches up with the tortoise or a cycle is detected. If a cycle is detected, reset the tortoise and move the hare back to its position before the reset.

Phase 2 (Cycle Start Detection):
Move the tortoise and hare one step at a time until they match again. The position where they match again is the starting point of the cycle, corresponding to the duplicate element.

# Let's explain why this works for the problem at hand:

Properties of Floyd's Tortoise and Hare Algorithm:
The algorithm ensures that the tortoise and hare will match again at some position in the list. Exploiting this property, if a cycle exists, the tortoise and hare will certainly match at some position within the cycle.

Relation between Duplicate Element and Cycle:
In the presence of a duplicate element, the duplicate corresponds to the starting point of the cycle. Starting from the first element as the tortoise, and moving through the duplicates until reaching a duplicate (cycle start), the hare will join, and the tortoise and hare will match again inside the cycle.

Therefore, the Floyd's Tortoise and Hare Algorithm provides an efficient and reliable way to find duplicate elements.
