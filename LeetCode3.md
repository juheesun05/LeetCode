# LeetCode 3_Longest Substring Without Repeating Characters
## 문제 입출력 예시 및 제약조건
Example 1:
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.

Example 2:
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
 
Constraints:
0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.

## 코드
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int> m(128, -1); // 초기화
        int left = 0, maxLength = 0;

        for (int right = 0; right < s.length(); right++) {
            // 현재 문자가 이전에 있었으면 left 포인터를 업데이트
            if (m[s[right]] >= left) {
                left = m[s[right]] + 1;
            }
            
            // 현재 문자 업데이트
            m[s[right]] = right;
            
            // 길이 계산 후 최댓값 저장
            maxLength = max(maxLength, right - left + 1);
        }

        return maxLength; // maxLength 반환
    }
};
```
