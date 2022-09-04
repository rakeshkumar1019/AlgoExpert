Question Lin: https://leetcode.com/problems/reverse-nodes-in-k-group/

Approch: Recursive | time O(n) | space O(n/k)

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
    ListNode *reverseKGroupHelper(ListNode* head, int k, int len){
         if( head == nullptr || len < k ) return head;
          ListNode *prev = nullptr;
          ListNode *curr = head;
          ListNode *forward = nullptr;
          int numberOfNode = 1;       
          int count = 0;
          while( curr != nullptr  && count < k ){
            forward = curr->next;
            curr->next = prev;
            prev = curr;
            curr = forward;
            count ++;
          }

          if( forward != nullptr ){
            head->next = reverseKGroupHelper(forward,k,len-k);
          }
          return prev;
    }
    ListNode* reverseKGroup(ListNode* head, int k) {
        if( head == nullptr ) return nullptr;
        int len = 0;
        ListNode *temp = head;
        while ( temp != nullptr ){
            len++;
            temp = temp->next;
        }
        return reverseKGroupHelper(head,k,len);
         
    }
};
```
