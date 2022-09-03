T.C: O(max(n,m)). | S.C :O(max(n,m))

```cpp
using namespace std;

// This is an input struct. Do not edit.
class LinkedList {
public:
  int value;
  LinkedList *next = nullptr;

  LinkedList(int value) { this->value = value; }
};

LinkedList *reverseLL( LinkedList *head){
  if( head == nullptr ) return head;
  LinkedList *prev = nullptr;
  LinkedList *curr = head;
  LinkedList *forward = nullptr;
  while( curr != nullptr ){
    forward = curr->next;
    curr->next = prev;
    prev = curr;
    curr = forward;
  }
  return prev;
}
void insertAtEnd(LinkedList *&head, LinkedList *&tail , int digit ){
  cout<<digit<<endl;
  LinkedList * node = new LinkedList(digit);
  if( head == nullptr ){
    head = node;
    tail = node;
    return;
  } else {
    tail->next = node;
    tail = node;
  }
}
LinkedList *addTwoNumber(LinkedList *one , LinkedList *two ){
  int carry = 0;
  LinkedList *head = nullptr;
  LinkedList *tail = nullptr;
  while( one != nullptr && two != nullptr ){
    int sum = one->value + two->value + carry;
    // cout<<"sum"<<sum<<endl;
    int digit = sum%10;
    insertAtEnd(head,tail,digit);
    carry = sum/10;  
    one = one->next;
    two = two->next;
  }
   while( one != nullptr ){
    int sum = one->value + carry;
    int digit = sum % 10;
    insertAtEnd(head,tail,digit);
    carry = sum/10;  
    one = one->next;
  }
  while( two != nullptr ){
    int sum = two->value + carry;
    int digit = sum%10;
    insertAtEnd(head,tail,digit);
    carry = sum/10;  
    two = two->next;
  }
  while( carry > 0 ){
    int sum = carry;
    int digit = sum%10;
    insertAtEnd(head,tail,digit);
    carry = sum / 10;  
  }
  return head;
}
LinkedList *sumOfLinkedLists(LinkedList *one, LinkedList *two) {
  // if( one == nullptr && two == nullptr ) return nullptr;
  // LinkedList *oneLL = reverseLL(one);
  // LinkedList *twoLL = reverseLL(two);
  LinkedList *additionHead = addTwoNumber(one,two);
  // additionHead = reverseLL(additionHead);
  return additionHead;
}
```
