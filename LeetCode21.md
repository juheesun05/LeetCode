```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {

        // 시작용 더미 노드
        ListNode dummy(0);

        // 현재 연결할 위치
        ListNode* tail = &dummy;

        // 둘 다 남아있는 동안 비교
        while (list1 != nullptr && list2 != nullptr) {

            if (list1->val < list2->val) {
                tail->next = list1;
                list1 = list1->next;
            }
            else {
                tail->next = list2;
                list2 = list2->next;
            }

            // 한 칸 이동
            tail = tail->next;
        }

        // 남은 리스트 붙이기
        if (list1 != nullptr) {
            tail->next = list1;
        }
        else {
            tail->next = list2;
        }

        return dummy.next;
    }
};
