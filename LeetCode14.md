# LeetCode 14_Longest Common Prefix
## 문제 입출력 예시 및 제약조건

Example 1:
Input: strs = ["flower","flow","flight"]
Output: "fl"

Example 2:
Input: strs = ["dog","racecar","car"]
Output: ""

Explanation: There is no common prefix among the input strings.
 
Constraints:
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters if it is non-empty.

## 코드
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) return ""; // 입력값 비어있는지 확인
        string prefix = strs[0]; // 첫 번째 단어를 prefix로 

        for (int i = 1; i < strs.size(); i++) { // 두번째 단어부터 마지막 단어까지 prefix와 비교
            while (strs[i].find(prefix) != 0) { // 현재 단어에서 prefix가 어디에 위치해있는지 찾기, 0이아니면 prefix가 아님 따라서 0이 아닐동안만 반복
                prefix = prefix.substr(0, prefix.length() - 1); // prefix의 마지막 글차 지우기

                if (prefix.empty()) return ""; // 빈문자열이면 prefix가 없다는 것
            }
        }

        return prefix; // prefix 반환
    }
};
```
