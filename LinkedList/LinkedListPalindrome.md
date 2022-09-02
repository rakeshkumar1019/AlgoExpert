Approch 1 : using Array | time O(n) | space O(n)

```cpp
using namespace std;

// This is an input struct. Do not edit.
class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value) {
    this->value = value;
    this->next = nullptr;
  }
};
bool isPalindrome(vector<int> &arr){
  int n= arr.size();
  if( n == 1 ) return true;
  int left = 0;
  int right = n-1;
  while ( left <= right ){
    if( arr[left] == arr[right] ){
      left ++ ;
      right -- ;
    } else {
      return false;
    }
  }
  return true;
}
//Approch 1 : using array time O(n) | space O(n)
bool linkedListPalindrome(LinkedList *head) {
   if( head == nullptr || head->next == nullptr ) {
     return true;
   }
  LinkedList *temp = head;
  vector<int> arr;
  while( temp != nullptr ){
    arr.push_back(temp->value);
    temp = temp->next;
  }
  return isPalindrome(arr);
}

```

Approch 2 : using middle & reverse function | time O(n) | space O(1)

```cpp
using namespace std;

// This is an input struct. Do not edit.
class LinkedList {
public:
  int value;
  LinkedList *next;

  LinkedList(int value) {
    this->value = value;
    this->next = nullptr;
  }
};
LinkedList *findMiddle( LinkedList *head ){
  if( head == nullptr ) return head;
  if( head->next == nullptr ) return head;
  if( head->next->next == nullptr ) return head;
  LinkedList *slow = head->next;
  LinkedList *fast = head->next->next;

  while( fast->next != nullptr && fast->next->next != nullptr ){
    slow = slow->next;
    fast = fast->next->next;
  }
  return slow;
}
LinkedList *reverseLL(LinkedList *head){
  if( head == nullptr || head->next == nullptr ) return head;
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
//Approch2: using pointers | time O(n)  | space O(1)
bool linkedListPalindrome(LinkedList *head) {
  if ( head == nullptr || head->next == nullptr ) return true;
  //step 1 : find middle node
  LinkedList *middleNode = findMiddle(head);
  LinkedList *middleNextNode = middleNode->next;
  //step 2: reverse ll from middle next node
  LinkedList *reversedMiiddleNextNode = reverseLL(middleNextNode);
  //step 3: compare two halves
  LinkedList *h1 = head;
  LinkedList *h2 = reversedMiiddleNextNode;

  while( h2 != nullptr ){
    if( h1->value  == h2->value ){
      h1 = h1->next;
      h2 = h2->next;
    }else{
      return false;
    }
  }

  //step 4: optional reverse the middle next again to make  input unchanged
  LinkedList *reversedMiiddleNextNode1 = reverseLL(middleNextNode);
  return true;
  
}

```
