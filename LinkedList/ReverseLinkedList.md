T.C : O(n)

S.C : O(1)

```cpp
using namespace std;

class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value) {
    this->value = value;
    this->next = nullptr;
  }
};

LinkedList *reverseLinkedList(LinkedList *head) {
  if(head == nullptr || head->next == nullptr){
    return head;
  }

  LinkedList* prev=nullptr;
  LinkedList* curr=head;
  LinkedList* forward= nullptr;

  while(curr != nullptr){
    forward=curr->next;
    curr->next=prev;
    prev=curr;
    curr=forward;
  }
  return prev;
}

```
