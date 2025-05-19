C++ Data Structures and Algorithms Codes
========================================

1.  Linked List

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#include <iostream>

using namespace std;
struct Node {
    int data;
    Node * next;
};
class LinkedList {
    private: Node * head;
    public: LinkedList() {
        head = nullptr;
    }
    bool isEmpty() {
        return head == nullptr;
    }
    void insertAtFirst(int value) {
        Node * newNode = new Node {
            value,
            head
        };
        head = newNode;
    }
    void insertAtEnd(int value) {
        Node * newNode = new Node {
            value,
            nullptr
        };
        if (isEmpty()) {
            head = newNode;
            return;
        }
        Node * temp = head;
        while (temp -> next != nullptr)
            temp = temp -> next;
        temp -> next = newNode;
    }
    void display() {
        if (isEmpty()) {
            cout << "List is empty.\n";
            return;
        }
        Node * temp = head;
        while (temp != nullptr) {
            cout << temp -> data << " -> ";
            temp = temp -> next;
        }
        cout << "NULL\n";
    }
    int count() {
        int cnt = 0;
        Node * temp = head;
        while (temp != nullptr) {
            cnt++;
            temp = temp -> next;
        }
        return cnt;
    }
    bool search(int value) {
        Node * temp = head;
        while (temp != nullptr) {
            if (temp -> data == value)
                return true;
            temp = temp -> next;
        }
        return false;
    }
    void insertBefore(int target, int value) {
        if (isEmpty()) return;
        if (head -> data == target) {
            insertAtFirst(value);
            return;
        }
        Node * prev = nullptr;
        Node * curr = head;
        while (curr != nullptr && curr -> data != target) {
            prev = curr;
            curr = curr -> next;
        }
        if (curr == nullptr) {
            cout << "Value " << target << " not found.\n";
            return;
        }
        Node * newNode = new Node {
            value,
            curr
        };
        prev -> next = newNode;
    }
};
int main() {
    LinkedList list;
    list.insertAtEnd(10);
    list.insertAtEnd(20);
    list.insertAtFirst(5);
    list.insertBefore(10, 8);
    cout << "List contents:\n";
    list.display();
    cout << "Number of nodes: " << list.count() << endl;
    cout << "Search 20: " << (list.search(20) ? "Found" : "Not found") << endl;
    cout << "Search 100: " << (list.search(100) ? "Found" : "Not found") << endl;
    return 0;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Stack

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#include <iostream>

using namespace std;
#define MAX_SIZE 1000 // Maximum size of stack
class Stack {
    private: int top;
    int arr[MAX_SIZE];
    public: Stack() {
        top = -1;
    }
    bool push(int x) {
        if (top >= MAX_SIZE - 1) {
            cout << "Stack is full" << endl;
            return false;
        }
        arr[++top] = x;
        return true;
    }
    int pop() {
        if (top < 0) {
            cout << "Stack underflow" << endl;
            return 0;
        }
        return arr[top--];
    }
    int peek() {
        if (top < 0) {
            cout << "Stack is empty" << endl;
            return 0;
        }
        return arr[top];
    }
    bool isEmpty() {
        return (top < 0);
    }
    void display() {
        if (top < 0) {
            cout << "Stack is empty" << endl;
            return;
        }
        cout << "\nStack elements: ";
        for (int i = top; i >= 0; i--)
            cout << arr[i] << " ";
        cout << endl;
    }
};
int main() {
    cout << "Create a stack object:\n";
    Stack s;
    cout << "Check the stack is empty or not? ";
    cout << s.isEmpty() << endl;
    cout << "\nInsert some elements onto the stack:\n";
    s.push(7);
    s.push(6);
    s.push(5);
    s.push(4);
    s.display();
    cout << "\nRemove an element from the stack! ";
    cout << s.pop();
    s.display();
    cout << "\nTop of the element of the stack:\n";
    cout << s.peek();
    cout << endl;
    return 0;
}#include <iostream>

using namespace std;
struct Node {
    int data;
    Node * next;
};
class LinkedList {
    private: Node * head;
    public: LinkedList() {
        head = nullptr;
    }
    bool isEmpty() {
        return head == nullptr;
    }
    void insertAtFirst(int value) {
        Node * newNode = new Node {
            value,
            head
        };
        head = newNode;
    }
    void insertAtEnd(int value) {
        Node * newNode = new Node {
            value,
            nullptr
        };
        if (isEmpty()) {
            head = newNode;
            return;
        }
        Node * temp = head;
        while (temp -> next != nullptr)
            temp = temp -> next;
        temp -> next = newNode;
    }
    void display() {
        if (isEmpty()) {
            cout << "List is empty.\n";
            return;
        }
        Node * temp = head;
        while (temp != nullptr) {
            cout << temp -> data << " -> ";
            temp = temp -> next;
        }
        cout << "NULL\n";
    }
    int count() {
        int cnt = 0;
        Node * temp = head;
        while (temp != nullptr) {
            cnt++;
            temp = temp -> next;
        }
        return cnt;
    }
    bool search(int value) {
        Node * temp = head;
        while (temp != nullptr) {
            if (temp -> data == value)
                return true;
            temp = temp -> next;
        }
        return false;
    }
    void insertBefore(int target, int value) {
        if (isEmpty()) return;
        if (head -> data == target) {
            insertAtFirst(value);
            return;
        }
        Node * prev = nullptr;
        Node * curr = head;
        while (curr != nullptr && curr -> data != target) {
            prev = curr;
            curr = curr -> next;
        }
        if (curr == nullptr) {
            cout << "Value " << target << " not found.\n";
            return;
        }
        Node * newNode = new Node {
            value,
            curr
        };
        prev -> next = newNode;
    }
};
int main() {
    LinkedList list;
    list.insertAtEnd(10);
    list.insertAtEnd(20);
    list.insertAtFirst(5);
    list.insertBefore(10, 8);
    cout << "List contents:\n";
    list.display();
    cout << "Number of nodes: " << list.count() << endl;
    cout << "Search 20: " << (list.search(20) ? "Found" : "Not found") << endl;
    cout << "Search 100: " << (list.search(100) ? "Found" : "Not found") << endl;
    return 0;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Reverse String using Stack

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#include <iostream>

#include <stack>

using namespace std;
string reverse(string s) {
    stack < char > st;
    for (char c: s)
        st.push(c);
    string res;
    while (!st.empty()) {
        res += st.top();
        st.pop();
    }
    return res;
}
int main() {
    string s = "Welcome";
    cout << s << endl;
    cout << reverse(s) << endl;
    return 0;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Bubble Sort

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#include <iostream>

using namespace std;
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}
int main() {
    int arr[] = {
        64,
        25,
        12,
        22,
        11
    };
    int n = sizeof(arr) / sizeof(arr[0]);
    bubbleSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Insertion Sort

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#include <iostream>

using namespace std;
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
int main() {
    int arr[] = {
        12,
        11,
        13,
        5,
        6
    };
    int n = sizeof(arr) / sizeof(arr[0]);
    insertionSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  Selection Sort

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#include <iostream>

using namespace std;
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int min_idx = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[min_idx])
                min_idx = j;
        }
        swap(arr[i], arr[min_idx]);
    }
}
int main() {
    int arr[] = {
        29,
        10,
        14,
        37,
        13
    };
    int n = sizeof(arr) / sizeof(arr[0]);
    selectionSort(arr, n);
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    return 0;
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
