# practicals
prac no 8 binary tree ds
code :
#include <iostream>

using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(nullptr), right(nullptr) {}
};
Node* insert(Node* root, int val) {
    if (root == nullptr) {
        return new Node(val);
    }
    if (val < root->data) {
        root->left = insert(root->left, val);
    } else if (val > root->data) {
        root->right = insert(root->right, val);
    }
    return root;
}
void inorderTraversal(Node* root) {
    if (root != nullptr) {
        inorderTraversal(root->left);
        cout << root->data << " ";
        inorderTraversal(root->right);
    }
}
int main() {
    Node* root = nullptr;
    int values[] = {10, 12, 14, 16, 17, 19, 20};
    int n = sizeof(values) / sizeof(values[0]);
    for (int i = 0; i < n; ++i) {
        root = insert(root, values[i]);
    }
    cout << "--- Final Binary Search Tree Output ---\n";
    cout << "Elements inserted: {10, 12, 14, 16, 17, 19, 20}\n";
    cout << "The tree is a highly skewed (right-leaning) structure.\n\n";

    cout << "In-Order Traversal (Sorted Output): ";
    inorderTraversal(root);
    cout << "\n";

    return 0;
}
