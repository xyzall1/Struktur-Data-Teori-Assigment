# <h1 align="center">CPMK 2 - SubCPMK 5</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## CPMK 2 - SubCPMK 5
1. Buatlah sebuah fungsi program untuk menghilangkan duplikasi data pada unsorted linked list (single atau double atau circular) (40 Poin)

#### Jawaban
``` C++
#include <iostream>
#include <unordered_set>
using namespace std;

// Struktur untuk node linked list
struct Node {
    int data;
    Node* next;
    Node(int value) : data(value), next(nullptr) {}
};

// Fungsi untuk menghilangkan duplikasi pada linked list
void removeDuplicates(Node* head) {
    
    if (head == nullptr || head->next == nullptr)
        return;

    
    unordered_set<int> seen;

    
    Node* curr = head;
    Node* prev = nullptr;

    // Loop hingga akhir linked list
    while (curr != nullptr) {
        // Jika nilai node saat ini telah ditemukan sebelumnya
        if (seen.find(curr->data) != seen.end()) {
            // Hapus node saat ini dan lanjutkan ke node berikutnya
            prev->next = curr->next;
            delete curr;
            curr = prev->next;
        } else {
            // Jika nilai node saat ini belum ditemukan, simpan nilai tersebut dan lanjutkan ke node berikutnya
            seen.insert(curr->data);
            prev = curr;
            curr = curr->next;
        }
    }
}

// Fungsi untuk mencetak linked list
void printList(Node* head) {
    
    Node* temp = head;

    // Loop hingga akhir linked list
    while (temp != nullptr) {
        
        cout << temp->data << " ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    // Membuat linked list
    Node* head = new Node(30);
    head->next = new Node(21);
    head->next->next = new Node(15);
    head->next->next->next = new Node(30);
    head->next->next->next->next = new Node(25);

    
    cout << "Linked List sebelum menghapus duplikat: ";
    printList(head);

    
    removeDuplicates(head);

    
    cout << "Linked List setelah menghapus duplikat: ";
    printList(head);

    return 0;
}
```

2. Buatlah sebuah algoritma dan fungsi program untuk menghapus node di tengah single linked list! (35 Poin)

#### Jawaban

```C++
#include <iostream>

using namespace std;


struct Node {
    int data;
    Node* next;
};

// Fungsi untuk menghapus node di tengah linked list
void deleteMiddleNode(Node** head, int position) {
    if (*head == NULL) {
        return;
    }

    Node* current = *head;
    for (int i = 1; i < position - 1; i++) {
        if (current->next == NULL) {
            return;
        }
        current = current->next;
    }

    if (current->next == NULL) {
        return;
    }

    Node* temp = current->next;
    current->next = current->next->next;
    delete temp;
}

// Fungsi untuk menampilkan linked list
void printList(Node* head) {
    while (head != NULL) {
        cout << head->data << " ";
        head = head->next;
    }
    cout << endl;
}

int main() {
    
    Node* head = new Node();
    head->data = 1;
    head->next = new Node();
    head->next->data = 3;
    head->next->next = new Node();
    head->next->next->data = 5;
    head->next->next->next = new Node();
    head->next->next->next->data = 7;
    head->next->next->next->next = new Node();
    head->next->next->next->next->data = 9;

    
    cout << "Linked list sebelum menghapus node: ";
    printList(head);

    // Hapus node di tengah linked list
    deleteMiddleNode(&head, 3);

    
    cout << "Linked list setelah menghapus node: ";
    printList(head);

    return 0;
}

```

3. Buatlah sebuah program untuk mengecek apakah linked list adalah sebuah palindrom! (50 Poin)

#### Jawaban 
``` C++
#include <iostream>
#include <stack>
#include <string>

using namespace std;

int main() {
    
    string input;

    
    cout << "Kalimat : ";
    getline(cin, input);

    // Buat stack untuk menyimpan karakter
    stack<char> s;

    // Loop hingga semua karakter dalam input
    for (char c : input) {
        
        s.push(c);
    }

    // Variabel untuk menyimpan kalimat yang diurutkan
    string reversed = "";

    // Loop hingga stack kosong
    while (!s.empty()) {
        
        reversed += s.top();
        
        s.pop();
    }

    // Cek apakah kalimat asli sama dengan kalimat yang diurutkan
    if (input == reversed) {
        
        cout << "Kalimat tersebut adalah polindrom" << endl;
    } else {
        
        cout << "Kalimat tersebut adalah bukan polindrom." << endl;
    }

    return 0;
}
```