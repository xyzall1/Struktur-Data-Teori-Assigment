# <h1 align="center">Graph & Tree</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Penjelasan 
Suatu pohon adalah graf tak berarah terhubungkan yang tidak memiliki rangkaian sederhana. Pohon adalah bentuk grafis unik yang banyak digunakan untuk berbagai tujuan. Jenis grafik yang disebut sebagai pohon mencakup struktur organisasi suatu perusahaan, silsilah suatu keluarga, skema sistem gugur suatu pertandingan, dan ikatan kimia suatu molekul. Pada pohon, simpul yang berderajat satu disebut daun (leave), simpul yang berderajat lebih besar daripada satu disebut simpul cabang (branch node) atau simpul internal (internal node). Hutan, di mana banyak pohon terpisah satu sama lain, disebut hutan [1].
Perbedaan Utama antara grafik & pohon :
- Siklus : Sementara pohon tidak memiliki siklus, grafik dapat
- Konektivitas : Grafik mungkin memiliki banyak komponen, tetapi pohon selalu terhubung.
- Hierarki : Grafik tidak memiliki struktur hierarki, tetapi pohon memiliki satu titik yang ditunjuk sebagai akar.
- Aplikasi : Aplikasi seperti ilmu komputer, jaringan sosial, dan transportasi menggunakan grafik. Struktur data hierarki seperti sistem file dan dokumen XML sering menggunakan pohon [2]

## Contoh program
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


 ## Refrensi
 [1]A. Muntaha and N. 13505041, “Graf Pohon dan Implementasinya dalam beberapa persoalan.” Available: https://informatika.stei.itb.ac.id/~rinaldi.munir/Matdis/2006-2007/Makalah/Makalah0607-6.pdf

 [2]“Difference between graph and tree,” GeeksforGeeks, Jan. 01, 2019. https://www.geeksforgeeks.orgdifference-between-graph-and-tree/