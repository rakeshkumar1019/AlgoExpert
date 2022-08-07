```cpp
/**********************************************************

    Following is the Binary Tree Node class structure:

    template <typename T>
    class BinaryTreeNode {
      public :
        T data;
        BinaryTreeNode<T> *left;
        BinaryTreeNode<T> *right;

        BinaryTreeNode(T data) {
                this -> data = data;
                left = NULL;
                right = NULL;
        }
    };
    
***********************************************************/
void inOrderTraversal(BinaryTreeNode<int> *root,int &count){
    if(root!=NULL){
         inOrderTraversal(root->left,count);
        if(root->left==NULL && root->right==NULL) {
            count++;
        }
        inOrderTraversal(root->right,count);  
    }
}
int noOfLeafNodes(BinaryTreeNode<int> *root){
    if(root==NULL) return 0;
    int count=0;
    inOrderTraversal(root,count);
    return count;
}
```
