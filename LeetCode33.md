# LeetCode 33_Search in Rotated Sorted Array
## 문제 입출력 예시 및 제약조건
Example 1:
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4

Example 2:
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1

Example 3:
Input: nums = [1], target = 0
Output: -1

Constraints:
1 <= nums.length <= 5000
-104 <= nums[i] <= 104
All values of nums are unique.
nums is an ascending array that is possibly rotated.
-104 <= target <= 104

## 코드
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        // 이진탐색
        int left = 0;
        int right = nums.size() - 1;

        while (left <= right) { // 왼쪽 포인터가 오른쪽 포인터보다 작거나 같을때까지 반복
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) return mid; // 중간값이 target이면 인덱스 반환

            // 1. 왼쪽이 정렬되어 있는 경우
            if (nums[left] <= nums[mid]) {
                // target이 왼쪽 정렬 구간 안에 있는지 확인
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } 
            // 2. 오른쪽이 정렬되어 있는 경우
            else {
                // target이 오른쪽 정렬 구간 안에 있는지 확인
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }

        return -1; // 찾지 못한 경우
    }
};
```
