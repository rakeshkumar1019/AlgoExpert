Approch: Recursive |  TIME : O(N) | SPACE : O(N/K)

```cpp
using namespace std;

// This is an input struct. Do not edit.
class LinkedList {
public:
  int value;
  LinkedList *next = nullptr;

  LinkedList(int value) { this->value = value; }
};
// TIME : O(N) | SPACE : O(N/K)
// Dry Run
// 0->1->2->3->4->5->nullptr
//Step1: reverse k nodes i.e here k = 2
// 1->0  2->3->4->5->nullptr
//head is still pointing at the 0th node
// head = 0
// prev = 1
// forward = 2
//So, now we have to make the link from head->next to nodeSwap(forward)
// return prev (prev is the new node .i.e 1)
  LinkedList *nodeSwap(LinkedList *head) {
  if( head == nullptr ) return nullptr;
  LinkedList *prev = nullptr;
  LinkedList *curr = head;
  LinkedList *forward = nullptr;
  int k = 2; //2 nodes
  int count = 0;
  while( curr != nullptr  && count < k ){
    forward = curr->next;
    curr->next = prev;
    prev = curr;
    curr = forward;
    count ++;
  }

  if( forward != nullptr ){
    head->next = nodeSwap(forward);
  }
  return prev;
}

```
