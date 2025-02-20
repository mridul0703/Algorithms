# Morris Traversal

## Introduction
Morris Traversal is a tree traversal algorithm that **does not use recursion or a stack**. It modifies the tree temporarily to achieve an **O(1) space complexity** while maintaining **O(n) time complexity**. It is mainly used for **inorder** and **preorder** traversal of binary trees.

---

## Algorithm
Morris Traversal works by using **threaded binary trees**. The key idea is to create a temporary link (thread) to the inorder predecessor of the current node, which helps in backtracking.

### Steps for Morris Inorder Traversal:
1. Initialize the current node as the root.
2. If the current node has no left child, print the node and move to the right child.
3. Otherwise, find the inorder predecessor of the current node (rightmost node of the left subtree).\4. If the predecessor's right child is `NULL`, make the current node its right child and move to the left child.
5. If the predecessor's right child is already set to the current node, remove the thread, print the current node, and move to the right child.
6. Repeat until the entire tree is traversed.

### Steps for Morris Preorder Traversal:
1. Initialize the current node as the root.
2. If the current node has no left child, print the node and move to the right child.
3. Otherwise, find the inorder predecessor.
4. If the predecessor's right child is `NULL`, make the current node its right child, print the current node, and move to the left child.
5. If the predecessor's right child is already set to the current node, remove the thread and move to the right child.
6. Repeat until the entire tree is traversed.

---

## Pseudocode

### **Morris Inorder Traversal**
```plaintext
function MorrisInorder(root):
    current = root
    while current is not NULL:
        if current.left is NULL:
            print current.data
            current = current.right
        else:
            predecessor = current.left
            while predecessor.right is not NULL and predecessor.right != current:
                predecessor = predecessor.right

            if predecessor.right is NULL:
                predecessor.right = current
                current = current.left
            else:
                predecessor.right = NULL
                print current.data
                current = current.right
```

### **Morris Preorder Traversal**
```plaintext
function MorrisPreorder(root):
    current = root
    while current is not NULL:
        if current.left is NULL:
            print current.data
            current = current.right
        else:
            predecessor = current.left
            while predecessor.right is not NULL and predecessor.right != current:
                predecessor = predecessor.right

            if predecessor.right is NULL:
                predecessor.right = current
                print current.data
                current = current.left
            else:
                predecessor.right = NULL
                current = current.right
```

---

## C++ Implementation

### **Morris Inorder Traversal**
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

Node* createNode(int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

void morrisInorder(Node* root) {
    Node* current = root;
    while (current != NULL) {
        if (current->left == NULL) {
            cout << current->data << " ";
            current = current->right;
        } else {
            Node* predecessor = current->left;
            while (predecessor->right != NULL && predecessor->right != current)
                predecessor = predecessor->right;

            if (predecessor->right == NULL) {
                predecessor->right = current;
                current = current->left;
            } else {
                predecessor->right = NULL;
                cout << current->data << " ";
                current = current->right;
            }
        }
    }
}

int main() {
    Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    
    cout << "Morris Inorder Traversal: ";
    morrisInorder(root);
    return 0;
}
```

### **Morris Preorder Traversal**
```cpp
void morrisPreorder(Node* root) {
    Node* current = root;
    while (current != NULL) {
        if (current->left == NULL) {
            cout << current->data << " ";
            current = current->right;
        } else {
            Node* predecessor = current->left;
            while (predecessor->right != NULL && predecessor->right != current)
                predecessor = predecessor->right;

            if (predecessor->right == NULL) {
                predecessor->right = current;
                cout << current->data << " ";
                current = current->left;
            } else {
                predecessor->right = NULL;
                current = current->right;
            }
        }
    }
}
```

---

## Complexity Analysis
| Algorithm  | Time Complexity | Space Complexity |
|------------|---------------|-----------------|
| Morris Inorder | O(n) | O(1) |
| Morris Preorder | O(n) | O(1) |

---

## Advantages
- **O(1) space complexity** (does not use stack or recursion).
- **Efficient traversal** without modifying the tree permanently.

## Disadvantages
- **Modifies the tree temporarily**, which can be an issue in some applications.
- **Not well-suited for certain tree structures** where modification is restricted.

---

## Conclusion
Morris Traversal is a powerful technique for tree traversal **without recursion or extra space**. It is useful in scenarios where memory is constrained, but care must be taken due to its temporary modifications to the tree.

---

### **References**
- [Binary Tree Traversals - GeeksforGeeks](https://www.geeksforgeeks.org/inorder-tree-traversal-without-recursion-and-without-stack/)
