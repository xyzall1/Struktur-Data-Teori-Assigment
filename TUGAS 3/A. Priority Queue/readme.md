# <h1 align="center">Prority Queue</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Penjelasan 
Priority Queue adalah jenis struktur data yang menggunakan struktur Queue biasa [1]. Ataupun dapat disebut dengan suatu struktur data yang di mana di dalamnya disusun menurut nilai prioritasnya, biasanya elemen dengan nilai prioritas lebih tinggi akan didahulukan dibandingkan dengan nilai yang memiliki prioritas lebih rendah [2]. Pada sistem ini menggunakan FIFO (firs in firs out), yang masuk terlebih dahulu akan keluar dahulu. Berikut ilustrasinya:

![image](https://github.com/xyzall1/Struktur-Data-Teori-Assigment/assets/161272189/c1936a8b-1027-41e0-8898-e84d6f0f784f)

Pada gambar di atas terdapan antrean yang di mana memiliki elemen berupa 1, elemen ini ditambahkan pada antrean lebih dahulu sebelum elemen 2, jadi elemen 1 ini nantinya pertama yang akan dihapus dari antrean sesuai dengan sistem operasi FIFO [3]. 

- Jenis-jenis Queue
    - Simple Queque
    - Circular Queue
    - Priority Queue
    - Double-Ended Queue

- Operasi Queue
    - Enqueue
    - Dequeue
    - IsEmpty
    - IsFull
    - Peek
    - Initialize


## Contoh Program 
```C++
#include <iostream>
#include <algorithm>

int H[50];
int heapSize = -1;

int parent(int i) {
    return (i - 1) / 2;
}

int leftChild(int i) {
    return ((2 * i) + 1);
}

int rightChild(int i) {
    return ((2 * i) + 2);
}

void shiftUp(int i) {
    while (i > 0 && H[parent(i)] < H[i]) {
        std::swap(H[parent(i)], H[i]);
        i = parent(i);
    }
}

void shiftDown(int i) {
    int maxIndex = i;
    int l = leftChild(i);
    if (1 <= heapSize && H[l] > H[maxIndex]) {
        maxIndex = 1;
    }
    int r = rightChild(i);
    if (r <= heapSize && H[r] > H[maxIndex]) {
        maxIndex = r;
    }
    if (i != maxIndex) {
        std::swap(H[i], H[maxIndex]);
        shiftDown(maxIndex);
    }
}

void insert(int p) {
    heapSize = heapSize + 1;
    H[heapSize] = p;
    shiftUp(heapSize);
}

int extractMax() {
    int result = H[0];
    H[0] = H[heapSize];
    heapSize = heapSize - 1;
    shiftDown(0);
    return result;
}

void changePriority(int i, int p) {
    int oldp = H[i];
    H[i] = p;
    if (p > oldp) {
        shiftUp(i);
    } else {
        shiftDown(i);
    }
}

int getMax() {
    return H[0];
}

void remove(int i) {
    H[i] = getMax() + 1;
    shiftUp(i);
    extractMax();
}

int main() {
    int n;
    std::cout << "Input the number of elements: ";
    std::cin >> n;

    for (int i = 0; i < n; ++i) {
        int p;
        std::cout << "Input element " << i + 1 << ": ";
        std::cin >> p;
        insert(p);
    }

    std::cout << "Priority Queue : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }    
    std::cout << "\n";

    std::cout << "Node with maximum priority : " << extractMax() << "\n";

    std::cout << "Priority queue after extracting maximum : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }
    std::cout << "\n";

    int i;
    std::cout << "Input the index of the element to change priority: ";
    std::cin >> i;
    int p;
    std::cout << "Input the new priority: ";
    std::cin >> p;
    changePriority(i, p);

    std::cout << "Priority queue after priority change : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }
    std::cout << "\n";
    
    std::cout << "Input the index of the element to remove: ";
    std::cin >> i;
    remove(i);

    std::cout << "Priority queue after removing the element : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }
    return 0;
}
```
#### Interpretasi 
Kode di atas merupakan kode yang menerangkan tentang struktur data Prioroty Queue yang menggunakan heap. Heap sendiri digunakan untuk menampung elemen dengan prioritas yang berbeda, serta operasi-operasi seperti penghapusan serta penggantian prioritas lalu penghapusan elemen dapat dilakukan untuk menghemat waktu dengan yang lebih singkat.
Berikut alur programnya :
- Pertama, kita meminta user untuk memasukkan jumlah elemen yang ingin disimpan dalam heap.
- Kemudian kode akan menggunakan fungsi insert(p) untuk memasukkan elemen ke dalam heap dan menampilkan isi heap.
- Lalu kita menggunakan fungsi extractMax() untuk mengambil elemen dengan prioritas tertinggi dari heap dan menampilkannya.
- Selanjutnya, kita meminta user untuk memasukkan indeks elemen yang ingin diubah prioritasnya dan kode akan mengubah prioritasnya.

Berikut fungsi yang digunakan :
- parent(i): Fungsi ini mengembalikan indeks parent ke-i dalam heap dari node.
- leftChild(i) dan rightChild(i): Indeks anak kiri dan anak kanan dikembalikan dari node ke-i dalam heap melalui fungsi-fungsi ini.
- hiftUp(i): Fungsi ini digunakan untuk menggeser node ke-i ke atas dalam heap jika nilai node tersebut lebih besar dari nilai parent-nya.
- shiftDown(i): Jika nilai node ke-i lebih kecil dari nilai anak-nya, fungsi ini digunakan untuk menggeser node ke-i ke bawah dalam heap.
- insert(p): Fungsi ini digunakan untuk menyisipkan elemen baru ke dalam heap dengan prioritas p.
- extractMax(): Fungsi ini digunakan untuk mengambil elemen dengan prioritas tertinggi dari heap.
- changePriority(i, p): Fungsi ini digunakan untuk mengubah prioritas elemen ke-i dalam heap menjadi p.
- getMax(): Fungsi ini digunakan untuk mengambil elemen dengan prioritas yang paling tinggi dari heap.
- remove(i): Fungsi ini digunakan untuk menghapus elemen ke-i dari heap.

#### Output:
![unguided 1](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/ca1a982e-6674-4813-886f-01ecd49327ae)

Kode di atas akan menampilkan sebuah output berupa heap nya akan diinput manual oleh user. Pertama kita akan disuguhkan pesan "Input the number of elements" di sini kita diperintah untuk memasukkan jumlah elemen, kemudian akan muncul pesan "Input element" yang nantinya user diperintah untuk memasukkan elemen sampai dnegan jumlan elemen yang dimasukkan pertama kali tadi. Selanjutnya akan ditampilkan node tadi setelah itu akan dicari maximum priority yaitu 45. Kemudian node akan di extract setelah itu kita diberikan perintah untuk mengubah nilai dengan memasukkan elemen dan kita diarahkan untuk input nilai prioritas terbaru yaitu 49. Kemudian prority queue akan berubah menjadi [49 20 31 13 7 7 13 12] lalu kita akan menghapus elemen ke 3 serta hasil akhirnya yaitu [ 49 12 31 20 7 7 11].
 

 ## Refrensi
 [1]A. Nurcholis, S. Batara N, and M. Octamanullah, “Penerapan struktur data Heap Priority Queue pada algoritma Djikstra untuk mendapatkan kompleksitas O((n + m)log n).” Available: https://informatika.stei.itb.ac.id/~rinaldi.munir/Stmik/Makalah/MakalahStmik38.pdf


 [2]“Priority Queue | Set 1 (Introduction) - GeeksforGeeks,” GeeksforGeeks, Dec. 03, 2018. https://www.geeksforgeeks.org/priority-queue-set-1-introduction/

 [3]“Struktur Data Queue: Pengertian, Jenis, dan Kegunaannya,” Trivusi, Sep. 16, 2022. https://www.trivusi.web.id/2022/07/struktur-data-queue.html