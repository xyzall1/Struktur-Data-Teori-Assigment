# <h1 align="center">CPMK 2 - SubCPMK 6</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## CPMK 2 - SubCPMK 6
1. Tulislah sebuah program dari operasi stack seperti pop, push, isEmpty, isFull, dll(min 5)! (60 Poin)

#### Jawaban
``` C++
#include <iostream>

using namespace std;

// Struktur untuk node antrian
struct Node {
    string data;
    Node* next;
};

// Variabel untuk pointer awal dan akhir antrian
Node* front = nullptr;
Node* back = nullptr;
int count = 0;

// Konstanta untuk batas antrian
const int maksimalQueue = 5;

// Fungsi untuk mengecek apakah antrian penuh
bool isFull() {
    
    return count == maksimalQueue;
}

// Fungsi untuk mengecek apakah antrian kosong
bool isEmpty() {
    
    return count == 0;
}

// Fungsi untuk menambahkan data ke antrian
void enqueueAntrian(string data) {
    
    if (isFull()) {
        cout << "Antrian Penuh" << endl;
    } else {
        
        Node* newNode = new Node();
        newNode->data = data;
        newNode->next = nullptr;

        
        if (isEmpty()) {
            front = newNode;
            back = newNode;
        } else {
            
            back->next = newNode;
            back = newNode;
        }
        
        count++;
    }
}

// Fungsi untuk menghapus data dari antrian
void dequeueAntrian() {
    
    if (isEmpty()) {
        cout << "Antrian Kosong" << endl;
    } else {
        
        Node* temp = front;
        front = front->next;
        delete temp;
        
        count--;
        
        if (isEmpty()) {
            back = nullptr;
        }
    }
}

// Fungsi untuk menghitung jumlah antrian
int countQueue() {
    
    return count;
}

// Fungsi untuk menghapus semua data dari antrian
void clearQueue() {
    
    while (!isEmpty()) {
        dequeueAntrian();
    }
}

// Fungsi untuk menampilkan data antrian
void viewQueue() {
    
    Node* temp = front;
    int i = 1;
    cout << "Data antrian teller: " << endl;
   
    while (temp != nullptr) {
        cout << i << ". " << temp->data << endl;
        temp = temp->next;
        i++;
    }
}

int main() {
    
    enqueueAntrian("Aliana");
    enqueueAntrian("Sawafi");
    
    viewQueue();
   
    cout << "Jumlah antrian = " << countQueue() << endl;
    
    dequeueAntrian();
    
    viewQueue();
    
    cout << "Jumlah antrian = " << countQueue() << endl;
    
    clearQueue();
    
    viewQueue();
    
    cout << "Jumlah antrian = " << countQueue() << endl;
    return 0;
}
```

2. Tulislah sebuah program untuk mensortir sebuah stack, sehingga item dengan nilai terkecil menjadi top pada stack tersebut! Diperbolehkan menggunakan tambahan temporary stack, namun tidak diperbolehkan untuk menyalin dari struktur data yang lain seperti array.  Program stack yang dibuat dapat menggunakan operasi stack seperti push, pop, peek, dan isEmpty. (40 poin)

#### Jawaban

``` C++
#include <iostream>
#include <stack>
using namespace std;

// Fungsi untuk mengurutkan stack
void sortStack(stack<int>& s) {
    
    stack<int> tempStack;

    // Loop hingga stack kosong
    while (!s.empty()) {
        
        int temp = s.top();
        s.pop();

        
        while (!tempStack.empty() && tempStack.top() > temp) {
           
            s.push(tempStack.top());
            
            tempStack.pop();
        }

        
        tempStack.push(temp);
    }

    // Loop hingga stack sementara kosong
    while (!tempStack.empty()) {
        
        s.push(tempStack.top());
        
        tempStack.pop();
    }
}

// Fungsi untuk mencetak stack
void printStack(stack<int> s) {
    // Loop hingga stack kosong
    while (!s.empty()) {
        
        cout << s.top() << " ";
        
        s.pop();
    }
    cout << endl;
}

int main() {
    // Membuat stack
    stack<int> s;

    
    s.push(25);
    s.push(0);
    s.push(44);
    s.push(-4);
    s.push(-9);

    
    cout << "Stack sebelum disortir: ";
    printStack(s);

    // Mengurutkan stack
    sortStack(s);

   
    cout << "Stack setelah disortir: ";
    printStack(s);

    return 0;
}
```