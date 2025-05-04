# glut

## HELO BRUDA!!! NOTHING TO SEE HERE

TO CLEAR HISTORY : [Microsoft.PowerShell.PSConsoleReadLine]::ClearHistory()


// Practical 1: Telephone Book Using Hash Table (Linear & Quadratic Probing)
table, tableq = {}, {}
totl, totq = 0, 0

def create(b):
    for i in range(b):
        table[i] = -1
        tableq[i] = -1

def linsert(key, b):
    global totl
    hash = key % b
    flag = 0
    if table[hash] == -1:
        table[hash] = key
    else:
        for i in range(0, b):
            hash = (key + i) % b
            if table[hash] == -1:
                table[hash] = key
                totl += 1
                flag += 1
                break
        if flag == 0:
            print("Table Full or Key not probed.")

def qinsert(key, b):
    global totq
    hash = key % b
    flag = 0
    if tableq[hash] == -1:
        tableq[hash] = key
    else:
        for i in range(0, int((b - 1) / 2)):
            hash = (key + (i * i)) % b
            if tableq[hash] == -1:
                tableq[hash] = key
                totq += 1
                flag += 1
                break
        if flag == 0:
            print("Table Full or Key not probed.")

def lsearch(key, b):
    comparisons = 0
    hash = key % b
    if table[hash] == -1:
        print(f"Key : {key} is not present. Comparisons: {comparisons}")
    else:
        for i in range(0, b):
            comparisons += 1
            hash = (key + i) % b
            if table[hash] == -1:
                print(f"Key : {key} is not present. Comparisons: {comparisons}")
                break
            elif table[hash] == key:
                print(f"Key : {key} is present at location : {hash}. Comparisons: {comparisons}")
                break
        if comparisons == 0:
            print(f"Key : {key} is not present. Comparisons: {comparisons}")

def qsearch(key, b):
    comparisons = 0
    hash = key % b
    if tableq[hash] == -1:
        print(f"Key : {key} is not present. Comparisons: {comparisons}")
    else:
        for i in range(0, int((b - 1) / 2)):
            comparisons += 1
            hash = (key + (i * i)) % b
            if tableq[hash] == -1:
                print(f"Key : {key} is not present. Comparisons: {comparisons}")
                break
            elif tableq[hash] == key:
                print(f"Key : {key} is present at location : {hash}. Comparisons: {comparisons}")
                break
        if comparisons == 0:
            print(f"Key : {key} is not present. Comparisons: {comparisons}")

def printtable(t1, b):
    print("Probed Table:")
    for i in range(b):
        print(t1[i], end="|")
    print("")

# New functions for display options:
def display_linear_table(b):
    print("Linear Probing Table:")
    for i in range(b):
        print(f"Index {i}: {table[i]}")

def display_quadratic_table(b):
    print("Quadratic Probing Table:")
    for i in range(b):
        print(f"Index {i}: {tableq[i]}")

b = int(input("Enter the table size: "))
create(b)

while True:
    ch = int(input("Enter 1-LP | 2-QP | 3-Display Linear Table | 4-Display Quadratic Table | 0-EXIT: "))
    
    if ch == 1:
        while True:
            ch2 = int(input("Enter 1-Insert | 2-Search | 0-Back: "))
            if ch2 == 1:
                if totl == b:
                    print("The table is already full.")
                else:
                    key = int(input("Enter the client phone number to be inserted: "))
                    linsert(key, b)
            elif ch2 == 2:
                key = int(input("Enter the client phone number to be searched: "))
                lsearch(key, b)
            elif ch2 == 0:
                print("GOING BACK")
                break
            printtable(table, b)

    elif ch == 2:
        while True:
            ch2 = int(input("Enter 1-Insert | 2-Search | 0-Back: "))
            if ch2 == 1:
                if totq == b:
                    print("The table is already full.")
                else:
                    key = int(input("Enter the client phone number to be inserted: "))
                    qinsert(key, b)
            elif ch2 == 2:
                key = int(input("Enter the client phone number to be searched: "))
                qsearch(key, b)
            elif ch2 == 0:
                print("GOING BACK")
                break
            printtable(tableq, b)

    elif ch == 3:
        display_linear_table(b)

    elif ch == 4:
        display_quadratic_table(b)

    elif ch == 0:
        print("EXITED")
        break

// Practical 2: Set ADT Implementation--------------------------------------------------------------------------------------------------------------------------------------------------
my_set=set(())
my_set1=set((3,5,7,9,6))
#print(my_set)
while True:
    print("--------------------SET AS AN ADT--------------------")
    print("1. Add (new Element) ")
    print("2. Remove (element) ")
    print("3. Contains (element) ")
    print("4. Size () , Iterator () ")
    print("5. Intersection of two sets")
    print("6. Union of two sets")
    print("7. Difference between two sets")
    print("8. Subset")
    print("9. Exit")
    choice=int(input("Enter your choice:"))
    if choice==1:
        num=int(input("Enter number you want to add:"))
        my_set.add(num)
        print(my_set)
        
    if choice==2:
        num=int(input("Enter number you want to remove:"))
        if num in my_set:
            my_set.remove(num)
            print(my_set)
        else:
            print("Element not present is set!!!")
        
    if choice==3:
        num=int(input("Enter no. u want to search:"))
        if num in my_set:
            print("Element is present in set")
        else:
            print("Element not present is set!!!")
    if choice==4:
        print("Size:",len(my_set))
        print("Iterator:",iter(my_set))
    if choice==5:
        print(my_set)
        print(my_set1)
        print("Elements present are:")
        for num in my_set:
            if num in my_set1:
                print(num)
    if choice==6:
        union_set=set(())
        union_set=my_set.union(my_set1)
        print("Union Set: ",union_set)
    if choice==7:
        diff_set=set(())
        diff_set=my_set-my_set1
        print("Difference between two sets:",diff_set)
    if choice==8:
        subset=set(())
        x=int(input("Enter No. of elements:"))
        for i in range(x):
            num=int(input("Enter number you want to add:"))
            subset.add(num)
            print(subset)
        if subset in my_set:
            print(subset)
            print("Subset is present")
            print(my_set)
        if subset not in my_set:
            print("Subset not present")
    if choice==9:
        print("Exited!!")
        break
    if choice>=9:
        print("Invalid Choice!!!")
// Practical 3: Binary Search Tree Operations-------------------------------------------------------------------------------------------------------------------------------------------
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

Node* createNode(int data) {
    Node* newNode = new Node();
    if (!newNode) {
        cout << "Memory error\n";
        return NULL;
    }
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

Node* insertNode(Node* root, int data) {
    if (root == NULL) {
        root = createNode(data);
        return root;
    }

    if (data < root->data) {
        root->left = insertNode(root->left, data);
    } else if (data > root->data) {
        root->right = insertNode(root->right, data);
    }

    return root;
}

void inOrderTraversal(Node* root) {
    if (root != NULL) {
        inOrderTraversal(root->left);
        cout << root->data << " ";
        inOrderTraversal(root->right);
    }
}

int findLongestPath(Node* root) {
    if (root == NULL) {
        return 0;
    }

    int leftHeight = findLongestPath(root->left);
    int rightHeight = findLongestPath(root->right);

    if (leftHeight > rightHeight) {
        return leftHeight + 1;
    } else {
        return rightHeight + 1;
    }
}

Node* findSmallest(Node* root) {
    while (root->left != NULL) {
        root = root->left;
    }
    return root;
}

void swapNodes(Node* root) {
    if (root == NULL) {
        return;
    }

    Node* temp = root->left;
    root->left = root->right;
    root->right = temp;

    swapNodes(root->left);
    swapNodes(root->right);
}

Node* searchNode(Node* root, int val) {
    if (root == NULL || root->data == val) {
        return root;
    }

    if (val < root->data) {
        return searchNode(root->left, val);
    } else {
        return searchNode(root->right, val);
    }
}

int main() {
    Node* root = NULL;

    int values[] = {50, 30, 20, 40, 70, 60, 80};
    int n = sizeof(values) / sizeof(values[0]);

    for (int i = 0; i < n; i++) {
        root = insertNode(root, values[i]);
    }

    int longestPathLen = findLongestPath(root);
    cout << "Length of the longest path: " << longestPathLen << endl;

    Node* smallestNode = findSmallest(root);
    cout << "Smallest value in the tree: " << smallestNode->data << endl;

    int searchVal = 40;
    Node* foundNode = searchNode(root, searchVal);
    if (foundNode != NULL) {
        cout << "Value " << searchVal << " found in the tree." << endl;
    } else {
        cout << "Value " << searchVal << " not found in the tree." << endl;
    }

    swapNodes(root);
    cout << "Tree after swapping nodes: " << endl;
    inOrderTraversal(root);
    cout << endl;

    return 0;
}

// Practical 4: Expression Tree from Prefix Expression------------------------------------------------------------------------------------------------------------------------------------
#include <iostream> 
#include <stack> 
using namespace std;
struct Node { 
    char data; 
    Node* left; 
    Node* right; 
    Node(char val) : data(val), left(nullptr), right(nullptr) {} 
}; 

Node* constructTree(string prefix){
    stack<Node*> st;
    for (int i=prefix.length()-1;i>=0;i--){
        Node* node=new Node(prefix[i]);
        if (isalnum(prefix[i])){
            st.push(node);
        } else {
            node->left=st.top();
            st.pop();
            node->right=st.top();
            st.pop();
            st.push(node);
        }
    }
    return st.top();
}

void postorder(Node* root){
    stack<Node*> st1,st2;
    st1.push(root);
    while(!st1.empty()){
        Node* node=st1.top();
        st1.pop();
        st2.push(node);
        if(node->left) st1.push(node->left);
        if(node->right) st1.push(node->right);
    }
    while(!st2.empty()){
        cout<<st2.top()->data<<" ";
        delete st2.top();
        st2.pop();
    }
}

int main(){
    string prefix = "+--a*bc/def";
    Node* root=constructTree(prefix);
    postorder(root);
    return 0;
}

// Practical 5: Dictionary using BST----------------------------------------------------------------------------------------------------------------------------------------------------
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;

struct Node {
    char key[50];
    char meaning[100];
    Node* left;
    Node* right;
    
    Node(const char* k, const char* m) {
        strcpy(key, k);
        strcpy(meaning, m);
        left = nullptr;
        right = nullptr;
    }
};

class Dictionary {
private:
    Node* root;
    int comparisons; // Track comparisons for search operations

    // Helper function to find minimum node
    Node* findMin(Node* node) {
        while (node->left != nullptr)
            node = node->left;
        return node;
    }

    // Helper function for node deletion
    Node* deleteNode(Node* root, const char* key) {
        if (root == nullptr) return root;

        int comparison = strcmp(root->key, key);
        if (comparison > 0)
            root->left = deleteNode(root->left, key);
        else if (comparison < 0)
            root->right = deleteNode(root->right, key);
        else {
            // Node with one or no child
            if (root->left == nullptr) {
                Node* temp = root->right;
                delete root;
                return temp;
            }
            else if (root->right == nullptr) {
                Node* temp = root->left;
                delete root;
                return temp;
            }
            
            // Node with two children
            Node* temp = findMin(root->right);
            strcpy(root->key, temp->key);
            strcpy(root->meaning, temp->meaning);
            root->right = deleteNode(root->right, temp->key);
        }
        return root;
    }

    void inorderTraversal(Node* root, bool ascending) const {
        if (root != nullptr) {
            if (ascending) {
                inorderTraversal(root->left, ascending);
                cout << root->key << ": " << root->meaning << endl;
                inorderTraversal(root->right, ascending);
            } else {
                inorderTraversal(root->right, ascending);
                cout << root->key << ": " << root->meaning << endl;
                inorderTraversal(root->left, ascending);
            }
        }
    }

    void cleanup(Node* root) {
        if (root != nullptr) {
            cleanup(root->left);
            cleanup(root->right);
            delete root;
        }
    }

public:
    Dictionary() : root(nullptr), comparisons(0) {}
    
    ~Dictionary() {
        cleanup(root);
    }

    void insert(const char* key, const char* meaning) {
        Node* newNode = new Node(key, meaning);
        if (root == nullptr) {
            root = newNode;
            return;
        }

        Node* current = root;
        Node* parent = nullptr;
        while (current != nullptr) {
            parent = current;
            int comparison = strcmp(key, current->key);
            if (comparison < 0)
                current = current->left;
            else if (comparison > 0)
                current = current->right;
            else {
                // Key already exists, update meaning
                strcpy(current->meaning, meaning);
                delete newNode;
                return;
            }
        }

        if (strcmp(key, parent->key) < 0)
            parent->left = newNode;
        else
            parent->right = newNode;
    }

    bool search(const char* key, char* meaning) {
        comparisons = 0;
        Node* current = root;
        while (current != nullptr) {
            comparisons++;
            int comparison = strcmp(key, current->key);
            if (comparison == 0) {
                strcpy(meaning, current->meaning);
                return true;
            }
            if (comparison < 0)
                current = current->left;
            else
                current = current->right;
        }
        return false;
    }

    bool remove(const char* key) {
        Node* temp = root;
        root = deleteNode(root, key);
        return temp != root;
    }

    void update(const char* key, const char* newMeaning) {
        Node* current = root;
        while (current != nullptr) {
            int comparison = strcmp(key, current->key);
            if (comparison == 0) {
                strcpy(current->meaning, newMeaning);
                return;
            }
            if (comparison < 0)
                current = current->left;
            else
                current = current->right;
        }
        cout << "Key not found for update." << endl;
    }

    void display(bool ascending = true) const {
        if (root == nullptr) {
            cout << "Dictionary is empty." << endl;
            return;
        }
        inorderTraversal(root, ascending);
    }

    int getLastSearchComparisons() const {
        return comparisons;
    }
};

int main() {
    Dictionary dict;
    char choice;
    
    do {
        cout << "\nDictionary Operations:\n";
        cout << "1. Add new word\n";
        cout << "2. Delete word\n";
        cout << "3. Update meaning\n";
        cout << "4. Search word\n";
        cout << "5. Display (Ascending)\n";
        cout << "6. Display (Descending)\n";
        cout << "7. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;
        cin.ignore();

        char key[50], meaning[100];
        
        switch (choice) {
            case '1':
                cout << "Enter word: ";
                cin.getline(key, 50);
                cout << "Enter meaning: ";
                cin.getline(meaning, 100);
                dict.insert(key, meaning);
                break;
                
            case '2':
                cout << "Enter word to delete: ";
                cin.getline(key, 50);
                if (dict.remove(key))
                    cout << "Word deleted successfully.\n";
                else
                    cout << "Word not found.\n";
                break;
                
            case '3':
                cout << "Enter word to update: ";
                cin.getline(key, 50);
                cout << "Enter new meaning: ";
                cin.getline(meaning, 100);
                dict.update(key, meaning);
                break;
                
            case '4':
                cout << "Enter word to search: ";
                cin.getline(key, 50);
                if (dict.search(key, meaning)) {
                    cout << "Meaning: " << meaning << endl;
                    cout << "Number of comparisons: " << dict.getLastSearchComparisons() << endl;
                } else
                    cout << "Word not found.\n";
                break;
                
            case '5':
                cout << "\nDictionary (Ascending):\n";
                dict.display(true);
                break;
                
            case '6':
                cout << "\nDictionary (Descending):\n";
                dict.display(false);
                break;
                
            case '7':
                cout << "Exited\n";
                break;
                
            default:
                cout << "Invalid choice!\n";
        }
    } while (choice != '7');
    
    return 0;
}
  


// Practical 6: Graph using Adjacency Matrix and Connectivity------------------------------------------------------------------------------------------------------------------------------
ASSIGNMENT 6 :
#include <iostream>
using namespace std;
string cities[50];
int adj_list[50][50] = {0};
int main() {
	int n;
	cout << "Please Enter number of cities: ";
	cin >> n;
	for (int i = 0; i < n; i++) {
		cout << "Enter city " << i + 1 << " : ";
 		cin >> cities[i];
	}
	cout << "\nYour cities are: " << endl;
	for (int i = 0; i < n; i++) {
 		cout << "City " << i + 1 << ": " << cities[i] << endl;
	}
	for (int i = 0; i < n; i++) {
 		for (int j = i + 1; j < n; j++) {
 			cout << "Enter distance between " << cities[i] << " and " << cities[j] << " : ";
 			cin >> adj_list[i][j];
 			adj_list[j][i] = adj_list[i][j];
 		}
	}
	cout << "\nAdjacency List representing flight costs ( Here the cost represented is
	per unit km ):" << endl;
	for (int i = 0; i < n; i++) {
 		cout << cities[i] << " -> ";
 			for (int j = 0; j < n; j++) {
 				if (adj_list[i][j] != 0) {
 					cout << "(" << cities[j] << ", " << adj_list[i][j] << ") ";
 				}
 			}
 			cout << endl;
	}
	cout<<"The Above flights are connected....";
	return 0;
}

// Practical 7: Minimum Spanning Tree (Prim's Algorithm)----------------------------------------------------------------------------------------------------------------------------------
 
#include <iostream> 
#include <vector> 
#include <queue> 
#include <limits.h> 
 
using namespace std; 
 
struct Edge { 
    int destination; 
    int cost; 
}; 
 
class Graph { 
public: 
    vector<string> cities = {"Mumbai", "Bengaluru", "Chennai", "Jaipur", "Pune", "Hyderabad"}; 
    vector<vector<Edge>> adjList; 
 
    Graph(int numCities) { 
        adjList.resize(numCities); 
    } 
 
    void addEdge(int city1, int city2, int cost) { 
        adjList[city1].push_back({city2, cost}); 
        adjList[city2].push_back({city1, cost}); 
    } 
 
    void primMST() { 
        int numCities = cities.size(); 
        vector<int> key(numCities, INT_MAX); 
        vector<int> parent(numCities, -1); 
        vector<bool> inMST(numCities, false); 
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq; 
 
        key[0] = 0; 
        pq.push({0, 0}); // {cost, city} 
 
        while (!pq.empty()) { 
            int u = pq.top().second; 
            pq.pop(); 
 
            inMST[u] = true; 
 
            for (const auto& edge : adjList[u]) { 
                int v = edge.destination; 
                int cost = edge.cost; 
 
                if (!inMST[v] && cost < key[v]) { 
                    key[v] = cost; 
                    pq.push({cost, v}); 
                    parent[v] = u; 
                } 
            } 
        } 
 
        printMST(parent, key); 
    } 
 
    void printMST(const vector<int>& parent, const vector<int>& key) { 
        cout << "Edge\tWeight\n"; 
        int totalCost = 0; 
        for (int i = 1; i < parent.size(); i++) { 
            cout << cities[parent[i]] << " - " << cities[i] << "\t" << key[i] << "\n"; 
            totalCost += key[i]; 
        } 
        cout << "Total minimum cost: " << totalCost << endl; 
    } 
}; 
 
int main() { 
    Graph g(6); // 6 cities 
 
    // Adding edges (city1, city2, cost) 
    g.addEdge(0, 1, 10); // Mumbai - Bengaluru 
    g.addEdge(0, 2, 15); // Mumbai - Chennai 
    g.addEdge(1, 2, 5);  // Bengaluru - Chennai 
    g.addEdge(1, 3, 12); // Bengaluru - Jaipur 
    g.addEdge(2, 3, 8);  // Chennai - Jaipur 
    g.addEdge(3, 4, 7);  // Jaipur - Pune 
    g.addEdge(4, 0, 6);  // Pune - Mumbai 
    g.addEdge(1, 5, 20); // Bengaluru - Hyderabad 
    g.addEdge(2, 5, 25); // Chennai - Hyderabad 
 
    g.primMST(); 
 
    return 0; 
} 

// Practical 8: Optimal Binary Search Tree (OBST)-----------------------------------------------------------------------------------------------------------------------------------------

#include <iostream> 
#include <vector> 
#include<limits> 
using namespace std; 
 
 
struct Node { 
    int key; 
    float prob; 
    Node* left; 
    Node* right; 
 
    Node(int k, float p) : key(k), prob(p), left(nullptr), right(nullptr) {} 
}; 
 
 
float sumProb(const vector<float>& p, int i, int j) { 
    float sum = 0; 
    for (int k = i; k <= j; ++k) { 
        sum += p[k]; 
    } 
    return sum; 
} 
 
float optimalCost(const vector<float>& p, int i, int j) { 
    if (j < i) return 0; 
    if (j == i) return p[i]; 
 
    float minCost = numeric_limits<float>::max(); 
 
    for (int r = i; r <= j; ++r) { 
        float cost = optimalCost(p, i, r - 1) + optimalCost(p, r + 1, j); 
        float totalCost = cost + sumProb(p, i, j); 
 
        if (totalCost < minCost) 
            minCost = totalCost; 
    } 
 
    return minCost; 
} 
 
Node* constructOBST(const vector<int>& keys, const vector<float>& p, int i, int j) { 
    if (j < i) return nullptr; 
 
    float minCost = numeric_limits<float>::max(); 
    int rootIndex = i; 
 
    for (int r = i; r <= j; ++r) { 
        float cost = optimalCost(p, i, r - 1) + optimalCost(p, r + 1, j); 
        float totalCost = cost + sumProb(p, i, j); 
 
        if (totalCost < minCost) { 
            minCost = totalCost; 
            rootIndex = r; 
        } 
    } 
 
    Node* root = new Node(keys[rootIndex], p[rootIndex]); 
    root->left = constructOBST(keys, p, i, rootIndex - 1); 
    root->right = constructOBST(keys, p, rootIndex + 1, j); 
 
    return root; 
} 
void inorder(Node* root) { 
    if (!root) return; 
    inorder(root->left); 
    cout << "Key: " << root->key << " (Prob: " << root->prob << ")\n"; 
    inorder(root->right); 
} 
 
int main() { 
     
    vector<int> keys = {10, 20, 30, 40, 50}; 
    vector<float> probabilities = {0.2, 0.2, 0.4, 0.15, 0.15}; 
 
    int n = keys.size(); 
    float cost = optimalCost(probabilities, 0, n - 1); 
    cout << "Cost of Optimal BST: " << cost << endl; 
 
    Node* root = constructOBST(keys, probabilities, 0, n - 1); 
    cout << "\nInorder Traversal of OBST:\n"; 
    inorder(root); 
 
    return 0; 
}

// Practical 9: AVL Tree----------------------------------------------------------------------------------------------------------------------------------------------------------------

#include <iostream>
#include <string>
using namespace std;
struct AVLNode {
 string key;
 string value;
 int height;
 AVLNode *left, *right;
};
class AVLTree {
public:
 AVLNode *root;
 AVLTree() : root(nullptr) {}
int height(AVLNode *node) {
 return node ? node->height : 0;
 }
 int balanceFactor(AVLNode *node) {
 return node ? height(node->left) - height(node->right) : 0;
 }
 AVLNode *rotateRight(AVLNode *y) {
 AVLNode *x = y->left;
 AVLNode *T = x->right;
 x->right = y;
 y->left = T;

 y->height = max(height(y->left), height(y->right)) + 1;
 x->height = max(height(x->left), height(x->right)) + 1;
 return x;
 }
 AVLNode *rotateLeft(AVLNode *x) {
 AVLNode *y = x->right;
 AVLNode *T = y->left;
 y->left = x;
 x->right = T;
 x->height = max(height(x->left), height(x->right)) + 1;
 y->height = max(height(y->left), height(y->right)) + 1;
 return y;
 } AVLNode *balance(AVLNode *node) {
 node->height = max(height(node->left), height(node->right)) + 1;
 int bf = balanceFactor(node);
 if (bf > 1 && balanceFactor(node->left) >= 0)
 return rotateRight(node);

 if (bf > 1 && balanceFactor(node->left) < 0) {
 node->left = rotateLeft(node->left);
 return rotateRight(node);
 }
 if (bf < -1 && balanceFactor(node->right) <= 0)
 return rotateLeft(node);

 if (bf < -1 && balanceFactor(node->right) > 0) {
 node->right = rotateRight(node->right);
 return rotateLeft(node);
 }
 return node;
 }
 AVLNode *insert(AVLNode *node, string key, string value) {
 if (!node)
 return new AVLNode{key, value, 1, nullptr, nullptr};
 if (key < node->key)
 node->left = insert(node->left, key, value);
 else if (key > node->key)
 node->right = insert(node->right, key, value);
 else
 node->value = value;
 return balance(node);
 }
 AVLNode *findMin(AVLNode *node) {
 while (node && node->left)
 node = node->left;
 return node;
 }
AVLNode *remove(AVLNode *node, string key) {
 if (!node)
 return nullptr;
 if (key < node->key)
 node->left = remove(node->left, key);
 else if (key > node->key)
 node->right = remove(node->right, key);
 else {
 if (!node->left || !node->right) {
 AVLNode *temp = node->left ? node->left : node->right;
 delete node;
 return temp;
 } else {
 AVLNode *temp = findMin(node->right);
 node->key = temp->key;
 node->value = temp->value;
 node->right = remove(node->right, temp->key);
 }
 }
 return balance(node);
 }
 void inorder(AVLNode *node) {
 if (!node)
 return;
 inorder(node->left);
 cout << "[" << node->key << ": " << node->value << "] ";
 inorder(node->right);
 }
 void reverseInorder(AVLNode *node) {
 if (!node)
 return;
 reverseInorder(node->right);
 cout << "[" << node->key << ": " << node->value << "] ";
 reverseInorder(node->left);
 }
 void displayAscending() {
 inorder(root);
 cout << endl;
 }
 void displayDescending() {
 reverseInorder(root);
 cout << endl;
 }
 bool search(AVLNode *node, string key, int &comparisons) {
 comparisons++;
 if (!node)
 return false;
 if (key == node->key)
 return true;
 if (key < node->key)
 return search(node->left, key, comparisons);
 return search(node->right, key, comparisons);
 }
};
int main() {
 AVLTree tree;
 int choice;
 do {
 cout << "\nDictionary Operations:\n";
 cout << "1. Add Keyword\n";
 cout << "2. Delete Keyword\n";
 cout << "3. Update Value\n";
 cout << "4. Display in Ascending Order\n";
 cout << "5. Display in Descending Order\n";
 cout << "6. Search Keyword\n";
 cout << "7. Exit\n";
 cin >> choice;
 switch (choice) {
 case 1: {
 string key, value;
 cout << "Enter keyword: ";
 cin >> key;
 cout << "Enter meaning: ";
 cin.ignore();
 getline(cin, value);
 tree.root = tree.insert(tree.root, key, value);
 break;
 }

 case 2: {
 string key;
 cout << "Enter keyword to delete: ";
 cin >> key;
 tree.root = tree.remove(tree.root, key);
 break;
 }

 case 3: {
 string key, value;
 cout << "Enter keyword to update: ";
 cin >> key;
 cout << "Enter new meaning: ";
 cin.ignore();
 getline(cin, value);
 tree.root = tree.insert(tree.root, key, value);
 break;
 }

 case 4:
 tree.displayAscending();
 break;
 case 5:
 tree.displayDescending();
 break;
 case 6: {
 string key;
 int comparisons = 0;
 cout << "Enter keyword to search: ";
 cin >> key;
 if (tree.search(tree.root, key, comparisons))
 cout << "Keyword found with " << comparisons << "
comparisons.\n";
 else
 cout << "Keyword not found after " << comparisons << "
comparisons.\n";
 break;
 }

 case 7:
 break;
 default:
 cout << "Invalid choice!\n";
 break;
 }
 } while (choice != 7);
 return 0;
}

// Practical 10: Hospital Priority Queue------------------------------------------------------------------------------------------------------------------------------------------------

#include <iostream> 
#include <queue> 
#include <vector> 
using namespace std; 
 
enum Priority {  
     High, 
     Medium,  
     Low 
     }; 
class Patient { 
public: 
    string Name; 
    int age; 
    Priority priority; 
     
    Patient(string name, int age, Priority priority) { 
        Name = name; 
        this->age = age; 
        this->priority = priority; 
    } 
}; 
 
class ComparePriority { 
    public: 
        bool operator()(const Patient& p1, const Patient& p2) { 
            return p1.priority > p2.priority;   
        } 
    }; 
int main() { 
     
    priority_queue<Patient, vector<Patient>, ComparePriority> pq; 
     
    int n;  
    cout << "Enter the number of patients: "; 
    cin >> n; 
 
    for (int i = 0; i < n; i++) { 
        string name; 
        int age; 
        int priorityInput; 
         
        cout << "Enter details for patient "  << ":\n"; 
        cout << "Name: "; 
        cin >> name; 
        cout << "Age: "; 
        cin >> age; 
        cout << "Priority (0 for High, 1 for Medium, 2 for Low): "; 
        cin >> priorityInput; 
 
        if (priorityInput < 0 || priorityInput > 2) { 
            cout << "Invalid priority input. Please enter a number between 0 and 2.\n"; 
            continue; 
        } 
 
 
        pq.push(Patient(name, age, static_cast<Priority>(priorityInput))); 
    } 
 
     
    cout << "\nPatients in priority order:\n"; 
    while (!pq.empty()) { 
        Patient p = pq.top(); 
        pq.pop(); 
        cout << "Name: " << p.Name << ", Age: " << p.age << ", Priority: " << p.priority << endl; 
    } 
 
    return 0; 
}

// Practical 11: Student Info using Sequential File---------------------------------------------------------------------------------------------------------------------------------------

#include<iostream>
#include<string>
#include<fstream>
using namespace std;

struct student {
    string name;
    int rollNo;
    char division;
    string Address;
};

void Addstudent() {
    ofstream file("students.dat.txt", ios::app);
    if (!file) {
        cout << "Error opening file!" << endl;
        return;
    }

    student s;
    cout << "Enter student name:" << endl;
    cin.ignore(); // To ignore any previous newline characters
    getline(cin, s.name); // To allow spaces in name

    cout << "Enter student rollNo:" << endl;
    cin >> s.rollNo;

    cout << "Enter Student division:" << endl;
    cin >> s.division;

    cout << "Enter student Address:" << endl;
    cin.ignore(); // To ignore any previous newline characters
    getline(cin, s.Address); // To allow spaces in address

    file << s.name << " " << s.rollNo << " " << s.division << " " << s.Address << endl;
    file.close();
    cout << "Student details added successfully!" << endl;
}

void deletestudent() {
    string filename = "students.dat.txt";
    string temp_filename = "temp.dat";

    ifstream file(filename);
    if (!file) {
        cout << "Error opening the original file!" << endl;
        return;
    }

    ofstream temp_file(temp_filename);
    if (!temp_file) {
        cout << "Error opening the temporary file!" << endl;
        return;
    }

    int roll_to_delete;
    cout << "Enter the roll number of the student to delete: ";
    cin >> roll_to_delete;

    bool student_found = false;
    student s;

    while (file >> s.name >> s.rollNo >> s.division >> s.Address) {
        if (s.rollNo == roll_to_delete) {
            student_found = true;
            cout << "Student with roll number " << roll_to_delete << " found and deleted.\n";
        } else {
            temp_file << s.name << " " << s.rollNo << " " << s.division << " " << s.Address << endl;
        }
    }

    file.close();
    temp_file.close();

    if (!student_found) {
        cout << "Student with roll number " << roll_to_delete << " not found.\n";
    }

    if (remove(filename.c_str()) != 0) {
        cout << "Error deleting the original file!" << endl;
        return;
    }

    if (rename(temp_filename.c_str(), filename.c_str()) != 0) {
        cout << "Error renaming the temporary file!" << endl;
    }

    cout << "The student record has been deleted and changes saved successfully.\n";
}

void displaystudent() {
    ifstream file("students.dat.txt");
    if (!file) {
        cout << "Error in opening file!" << endl;
        return;
    }

    string name;
    int rollNo;
    char division;
    string address;

    cout << "\nList of all students:\n";
    while (file >> name >> rollNo >> division >> address) {
        cout << "Name: " << name << ", Roll No: " << rollNo 
             << ", Division: " << division << ", Address: " << address << endl;
    }

    file.close();
}

int main() {
    int choice = 0;

    while (choice != 4) {
        // Display menu to the user
        cout << "\nEnter choice:\n";
        cout << "1. Add Student\n";
        cout << "2. Delete Student\n";
        cout << "3. Display Students\n";
        cout << "4. Exit\n";
        cin >> choice;

        switch (choice) {
        case 1:
            Addstudent();
            break;
        case 2:
            deletestudent();
            break;
        case 3:
            displaystudent();
            break;
        default:
            cout << "Invalid choice!" << endl;
            break;
        }
    }

    cout << "Exiting program." << endl;
    return 0;
}


// Practical 12: Employee Info using Indexed Sequential File------------------------------------------------------------------------------------------------------------------------------

#include <iostream>
#include <fstream>
#include <cstring>

using namespace std;

struct Employee {
    char name[50];
    int emp_id;
    float salary;
};

struct IndexRecord {
    int emp_id;
    long position; 
};

class EmployeeManagement {
private:
    fstream seqFile; 
    fstream indexFile; 

public:
    EmployeeManagement() {
        seqFile.open("EMP.DAT", ios::in | ios::out | ios::binary | ios::app);
        indexFile.open("IND.DAT", ios::in | ios::out | ios::binary | ios::app);
    }

    void addEmployee() {
        Employee emp;
        IndexRecord indRec;

        cout << "Enter Name: ";
        cin >> emp.name;
        cout << "Enter Employee ID: ";
        cin >> emp.emp_id;
        cout << "Enter Salary: ";
        cin >> emp.salary;

       
        seqFile.seekp(0, ios::end);
        long pos = seqFile.tellp();
        seqFile.write((char*)&emp, sizeof(emp));

        
        indRec.emp_id = emp.emp_id;
        indRec.position = pos;
        indexFile.write((char*)&indRec, sizeof(indRec));

        cout << "Employee added successfully.\n";
    }

    void deleteEmployee(int emp_id) {
        Employee emp;
        IndexRecord indRec;
        bool found = false;

        
        indexFile.seekg(0);
        while (indexFile.read((char*)&indRec, sizeof(indRec))) {
            if (indRec.emp_id == emp_id) {
                found = true;
               
                seqFile.seekp(indRec.position);
                emp.emp_id = -1; // Logical deletion
                seqFile.write((char*)&emp, sizeof(emp));
                cout << "Employee deleted successfully.\n";
                break;
            }
        }

        if (!found) {
            cout << "Employee not found.\n";
        }
    }

    void displayEmployee(int emp_id) {
        Employee emp;
        IndexRecord indRec;
        bool found = false;

        // Search for the employee in the index file
        indexFile.seekg(0);
        while (indexFile.read((char*)&indRec, sizeof(indRec))) {
            if (indRec.emp_id == emp_id) {
                found = true;
                seqFile.seekg(indRec.position);
                seqFile.read((char*)&emp, sizeof(emp));
                
                if (emp.emp_id != -1) { 
                    cout << "Name: " << emp.name << "\n";
                    cout << "Employee ID: " << emp.emp_id << "\n";
                    cout << "Salary: " << emp.salary << "\n";
                } else {
                    cout << "Employee record is deleted.\n";
                }
                break;
            }
        }

        if (!found) {
            cout << "Employee not found.\n";
        }
    }

    ~EmployeeManagement() {
        seqFile.close();
        indexFile.close();
    }
};

int main() {
    EmployeeManagement ems;
    int choice, emp_id;

    do {
        cout << "\n1. Add Employee\n2. Delete Employee\n3. Display Employee\n4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                ems.addEmployee();
                break;
            case 2:
                cout << "Enter Employee ID to delete: ";
                cin >> emp_id;
                ems.deleteEmployee(emp_id);
                break;
            case 3:
                cout << "Enter Employee ID to display: ";
                cin >> emp_id;
                ems.displayEmployee(emp_id);
                break;
            case 4:
                cout << "Exiting...\n";
                break;
            default:
                cout << "Invalid choice. Please try again.\n";
                break;
        }
    } while (choice != 4);

    return 0;
}

