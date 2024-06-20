# <h1 align="center">Graph & Tree</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Penjelasan 
Suatu pohon adalah graf tak berarah terhubungkan yang tidak memiliki rangkaian sederhana. Pohon adalah bentuk grafis unik yang banyak digunakan untuk berbagai tujuan. Jenis grafik yang disebut sebagai pohon mencakup struktur organisasi suatu perusahaan, silsilah suatu keluarga, skema sistem gugur suatu pertandingan, dan ikatan kimia suatu molekul. Pada pohon, simpul yang berderajat satu disebut daun (leave), simpul yang berderajat lebih besar daripada satu disebut simpul cabang (branch node) atau simpul internal (internal node). Hutan, di mana banyak pohon terpisah satu sama lain, disebut hutan [1].

Jenis Graph
- Graph Berarah
- Graph tak berarah
- Weighted graph
- unweighted graph

Jenis Treee 
- General tree
- Binary tree
- Balanced tree
- Binary search tree
  
Perbedaan Utama antara grafik & pohon :
- Siklus : Sementara pohon tidak memiliki siklus, grafik dapat
- Konektivitas : Grafik mungkin memiliki banyak komponen, tetapi pohon selalu terhubung.
- Hierarki : Grafik tidak memiliki struktur hierarki, tetapi pohon memiliki satu titik yang ditunjuk sebagai akar.
- Aplikasi : Aplikasi seperti ilmu komputer, jaringan sosial, dan transportasi menggunakan grafik. Struktur data hierarki seperti sistem file dan dokumen XML sering menggunakan pohon [2]

## Contoh program
1. Program Graph
``` C++
#include <iostream>
#include <vector>
#include <string>
#include <iomanip>

using namespace std;

int main() {
    int jumlahSimpul;
    cout << "Silakan masukkan jumlah simpul: ";
    cin >> jumlahSimpul;

    vector<string> namaSimpul(jumlahSimpul);
    vector<vector<int>> bobot(jumlahSimpul, vector<int>(jumlahSimpul));

    cout << "Silakan masukkan nama simpul" << endl;
    for (int i = 0; i < jumlahSimpul; i++) {
        cout << "Simpul " << i + 1 << ": ";
        cin >> namaSimpul[i];
    }

    cout << "Silakan masukkan bobot antar simpul" << endl;
    for (int i = 0; i < jumlahSimpul; i++) {
        for (int j = 0; j < jumlahSimpul; j++) {
            cout << namaSimpul[i] << "--> " << namaSimpul[j] << " = ";
            cin >> bobot[i][j];
        }
    }

    cout << endl;
    cout << setw(30) << "";
    for (int i = 0; i < jumlahSimpul; i++) {
        cout << setw(10) << namaSimpul[i];
    }
    cout << endl;
    for (int i = 0; i < jumlahSimpul; i++) {
        cout << setw(30) << namaSimpul[i];
        for (int j = 0; j < jumlahSimpul; j++) {
            cout << setw(10) << bobot[i][j];
        }
        cout << endl;
    }

    return 0;
}
```

## Interpretasi
Program ini menjalankan tentang graph & tree dengan alur kode dengan penjelasan berikut :
- Pertama, kita menggunakan perintah cout untuk meminta pengguna memasukkan jumlah simpul ke dalam graf.
- Kemudian menggunakan perintah cin untuk melihat input user dan menyimpannya dengan variabel jumlahSimpul.
- Lalu kode akan membuat vektor nama Simpul yang mengukur jumlah Simpul untuk menyimpan nama Simpul.
- Kemudian kode akan membuat sebuah vektor dua dimensi bobot dengan ukuran jumlahSimpul x jumlahSimpul untuk menyimpan bobot antar simpul.
- Selanjutnya, kode akan meminta user untuk input nama-nama simpul menggunakan perintah cout and cin, lalu nama simpul tadi disimpan di dalam vektor namaSimpul.
- Lalu diteruskan kode memrintahkan user untuk memasukkan bobot antar simpul menggunakan perintah cout. Matriks tersebut nantinya terdiri dari nama-nama simpul baris dan kolom serta bobot antar simpul.
- Kemudian yang terakhir, kode menggunakan perintah setw untuk mengatur lebar kolom dan baris dalam matriks, sehingga tampilannya rapi.

Berikut komponen dari kode di atas:
- JumlahSimpul : untuk menyimpan jumlah simpul dan graf
- namaSimpul : vektor untu menyimpan nama-nama simpul dalam graf
- bobot : vektor dua dimensi yang digunakan untuk menyimpan bobot antar simpul dalam graf

#### Output:
![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/da53b593-222b-4e5c-a936-07e5be5c18e5)
Kode di akan menjalankan hubungan antar simpul dalam sebuah jaringan, yang kode ini akan menjalankan output interaktif. Nantinya user diperintah untuk memasukkan sebuah jumlah simpul, nama simpul, lalu bobot antar simpul dan nantinya kode ini akan menampilkan sebual tabel yang nantinya tabel tersebut mempresentasikan sebuah simpul serta setiap kolom mempresentasikan bobot antar simpul dengan simpul lainnya. Nilai 0 menunjukkan bahwa tidak ada bobot antar simpul.

2. Program Tree
 ```C++
#include <iostream>
using namespace std;

struct TNode {
    int data;
    TNode *left;
    TNode *right;

    // constructor
    TNode(int value) {
        data = value;
        left = NULL;
        right = NULL;
    }
};

void preOrder(TNode *node) {
    if (node!= NULL) {
        cout << node->data << " ";
        preOrder(node->left);
        preOrder(node->right);
    }
}

void inOrder(TNode *node) {
    if (node!= NULL) {
        inOrder(node->left);
        cout << node->data << " ";
        inOrder(node->right);
    }
}

void postOrder(TNode *node) {
    if (node!= NULL) {
        postOrder(node->left);
        postOrder(node->right);
        cout << node->data << " ";
    }
}

void displayChild(TNode *node, int target) {
    if (node!= NULL) {
        if (node->data == target) {
            if (node->left!= NULL) {
                cout << "Child: " << node->left->data << endl;
            }
            if (node->right!= NULL) {
                cout << "Child: " << node->right->data << endl;
            }
        } else {
            displayChild(node->left, target);
            displayChild(node->right, target);
        }
    }
}

void displayDescendant(TNode *node, int target) {
    if (node!= NULL) {
        if (node->data == target) {
            preOrder(node);
        } else {
            displayDescendant(node->left, target);
            displayDescendant(node->right, target);
        }
    }
}

int main() {
    TNode *root = NULL;

    int choice;
    while (true) {
        cout << "Menu:" << endl;
        cout << "1. Input data tree" << endl;
        cout << "2. Tampilkan pre-order" << endl;
        cout << "3. Tampilkan in-order" << endl;
        cout << "4. Tampilkan post-order" << endl;
        cout << "5. Tampilkan child node" << endl;
        cout << "6. Tampilkan descendant node" << endl;
        cout << "7. Keluar" << endl;
        cout << "Pilihan: ";
        cin >> choice;

        switch (choice) {
            case 1: {
                int data;
                cout << "Input data tree: ";
                cin >> data;
                if (root == NULL) {
                    root = new TNode(data);
                } else {
                    TNode *temp = root;
                    while (true) {
                        if (data < temp->data) {
                            if (temp->left == NULL) {
                                temp->left = new TNode(data);
                                break;
                            } else {
                                temp = temp->left;
                            }
                        } else {
                            if (temp->right == NULL) {
                                temp->right = new TNode(data);
                                break;
                            } else {
                                temp = temp->right;
                            }
                        }
                    }
                }
                break;
            }
            case 2:
                preOrder(root);
                cout << endl;
                break;
            case 3:
                inOrder(root);
                cout << endl;
                break;
            case 4:
                postOrder(root);
                cout << endl;
                break;
            case 5: {
                int target;
                cout << "Input node target: ";
                cin >> target;
                displayChild(root, target);
                break;
            }
            case 6: {
                int target;
                cout << "Input node target: ";
                cin >> target;
                displayDescendant(root, target);
                cout << endl;
                break;
            }
            case 7:
                return 0;
            default:
                cout << "Pilihan tidak valid" << endl;
        }
    }

    return 0;
}
```

## Interpretasi
Kode program di atas menajalankan berupa tree. berikut alur program nya
- Program meminta user untuk memilih salah satu opsi dari menu utama.
- lalu jika user memilih opsi 1, maka program akan meminta user untuk input sata tree. data tree sendiri disimpan dalam struktur data tree.
- lalu jika memilih opsi 2,3, ataupun 4 maka kode akan menampilkan tree dalam urutan pre-order, in-order, atau post-order.
- lalu jika user memilih opsi 5, maka program akan meminta user untuk input node target, lalu kemudian akan ditampilkan ana dari node tersebut.
- jika user memilih opsi 6, program akan meminta user untuk input node target, kemudian menampilkan keturunan dari node tersebut
- terakhir, jika user memilih oosi 7 maka program akan keluar.

fungsi yang ditampilkan pada program seperti :
- preOrder: Menampilkan tree dalam urutan pre-order, yaitu node root dulu, kemudian anak kiri, dan terakhir anak kanan.
- inOrder: Menampilkan tree dalam urutan in-order, yaitu anak kiri dulu, kemudian node root, dan terakhir anak kanan.
- postOrder: Menampilkan tree dalam urutan post-order, yaitu anak kiri dan kanan dulu, kemudian node root.
- displayChild: Menampilkan anak dari sebuah node tertentu.
- displayDescendant: Menampilkan keturunan dari sebuah node tertentu.

#### Output:
![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/67aeb41d-f728-433b-b30a-274d46d12cc4)
Kode di akan menjalankan output interaktif di mana ada berupa pilihan input data tree, tampilkan pre-order, Tampilkan in-order, Tampilkan post-order,Tampilkan child node, Tampilkan descendant node, dan Keluar. Di mana nantinya user diperintahkan untuk memasukkan pilihan lalu input tree yang dimasukkan lalu diberikan pilihan untuk menampilkan tampilan tree jenis yang apa. Jika jenis child node dan descendent node maka user diperintahkan untuk memasukkan node target. Jika kode dirasa sudah cukup kode memiliki pilihan untuk keluar dari program untuk menyelesaikan program.



 ## Refrensi
 [1]A. Muntaha and N. 13505041, “Graf Pohon dan Implementasinya dalam beberapa persoalan.” Available: https://informatika.stei.itb.ac.id/~rinaldi.munir/Matdis/2006-2007/Makalah/Makalah0607-6.pdf

 [2]“Difference between graph and tree,” GeeksforGeeks, Jan. 01, 2019. https://www.geeksforgeeks.orgdifference-between-graph-and-tree/
