# LeetCode 7_Reverse Integer
## 문제 입출력 예시 및 제약조건
Example 1:
Input: x = 123
Output: 321

Example 2:
Input: x = -123
Output: -321

Example 3:
Input: x = 120
Output: 21

Constraints:
-2^31 <= x <= 2^31 - 1
--> max_value = 2147483647
--> min_value = -2147483648

## 코드
```cpp
class Solution 
 {
public:
    int reverse(int x) 
    {
        int reverse = 0; // 결과 저장할 변수
        while (x != 0) // x가 0이 될 때까지 한자리씩 계속 꺼내기 반복
        {
            int pop = x % 10; // x의 마지막 자리
            x /= 10; // x의 마지막 자리 제거

            if (reverse > INT_MAX / 10 || (reverse == INT_MAX / 10 && pop > 7)) return 0; // 마지막 자리 숫자 7
            if (reverse < INT_MIN / 10 || (reverse == INT_MIN / 10 && pop < -8)) return 0; // 마지막 자리 숫자 -8
            reverse = reverse * 10 + pop; // 역순
        }
        return reverse; // 결과 반환
        
    }
};
```
