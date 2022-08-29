Question Link: https://leetcode.com/problems/middle-of-the-linked-list

T.C: O(n)

S.C: O(1)

```cpp

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        if(head == nullptr || head->next == nullptr) {
            return head;
        }
        //for 2 node return second node
        if(head->next->next == nullptr){
            return head->next;
        }
        ListNode* slow = head;
        ListNode* fast = head;
        while( fast->next != nullptr && fast->next->next != nullptr ){
            slow=slow->next;
            fast=fast->next->next;
        }
        if(fast->next != nullptr) {
            return slow->next;
        }else{
           return slow; 
        }
    }
};
```
