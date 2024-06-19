# <h1 align="center">Hash Table</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Penjelasan 
Hash table merupakan algoritma yang memiliki kemampuan untyk menambah proses tambah, hapus, dan pencarian secara bersamaan, selain itu hash table sendiri memiliki kompleksitas waktu O(1) [1]. Teknik hash memungkinkan kita secara langsung mengakses data daftar dalam tabel dengan menghitung kunci, yang merupakan alamat daftar dalam tabel. Suatu data unik, yang dapat berupa nomor atau string karakter, disebut kunci.

!![image](https://github.com/xyzall1/Struktur-Data-Teori-Assigment/assets/161272189/ffaa3bdf-365a-4d83-b21c-0415c589b6b0)
Struktur dalam data tabel hash yaitu menyimpan elemen dalam pasangan nilai key di mana:
- Key : bilangan bulat yang digunakan untuk indeks nilai
- Nilai : sebuah data yang memiliki hubungan dengan key [2]

- Operasi Hash Table
    - Search : Mencari elemen pada hash table
    - Insert : Menyisipkan elemen pada hash table
    - Delete : Menghapus elemen pada hash table [3]




## Contoh Program 
```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class Mahasiswa {
public:
    string nim;
    int nilai;

    Mahasiswa(string nim, int nilai) {
        this->nim = nim;
        this->nilai = nilai;
    }
};

class HashTable {
private:
    vector<Mahasiswa*> table[10];

public:
    int hashFunction(string nim) {
        int hash = 0;
        for (char c : nim) {
            hash += c;
        }
        return hash % 10;
    }

    void tambahData(Mahasiswa* mahasiswa) {
        int index = hashFunction(mahasiswa->nim);
        table[index].push_back(mahasiswa);
    }

    void hapusData(string nim) {
        int index = hashFunction(nim);
        for (int i = 0; i < table[index].size(); i++) {
            if (table[index][i]->nim == nim) {
                table[index].erase(table[index].begin() + i);
                break;
            }
        }
    }

    Mahasiswa* cariDataNIM(string nim) {
        int index = hashFunction(nim);
        for (Mahasiswa* mahasiswa : table[index]) {
            if (mahasiswa->nim == nim) {
                return mahasiswa;
            }
        }
        return nullptr;
    }

    vector<Mahasiswa*> cariDataNilai(int nilaiAwal, int nilaiAkhir) {
        vector<Mahasiswa*> hasil;
        for (int i = 0; i < 10; i++) {
            for (Mahasiswa* mahasiswa : table[i]) {
                if (mahasiswa->nilai >= nilaiAwal && mahasiswa->nilai <= nilaiAkhir) {
                    hasil.push_back(mahasiswa);
                }
            }
        }
        return hasil;
    }
};

void tampilanMenu() {
    cout << "=============Pilih menu:==============" << endl;
    cout << "1. Tambah data" << endl;
    cout << "2. Hapus data" << endl;
    cout << "3. Cari data berdasarkan NIM" << endl;
    cout << "4. Cari data berdasarkan rentang nilai" << endl;
}

int main() {
    HashTable hashTable;
    while (true) {
        tampilanMenu();
        int pilihan;
        cout << "Masukkan pilihan Anda: ";
        cin >> pilihan;
        if (pilihan == 1) {
            string nim;
            int nilai;
            cout << "Masukkan NIM: ";
            cin >> nim;
            cout << "Masukkan nilai: ";
            cin >> nilai;
            Mahasiswa* mahasiswaBaru = new Mahasiswa(nim, nilai);
            hashTable.tambahData(mahasiswaBaru);
        } else if (pilihan == 2) {
            string nim;
            cout << "Masukkan NIM yang akan dihapus: ";
            cin >> nim;
            hashTable.hapusData(nim);
        } else if (pilihan == 3) {
            string nim;
            cout << "Masukkan NIM yang akan dicari: ";
            cin >> nim;
            Mahasiswa* mahasiswaDitemukan = hashTable.cariDataNIM(nim);
            if (mahasiswaDitemukan != nullptr) {
                cout << "Mahasiswa ditemukan: " << mahasiswaDitemukan->nim << ", " << mahasiswaDitemukan->nilai << endl;
            } else {
                cout << "Mahasiswa tidak ditemukan" << endl;
            }
        } else if (pilihan == 4) {
            int nilaiAwal, nilaiAkhir;
            cout << "Masukkan nilai awal: ";
            cin >> nilaiAwal;
            cout << "Masukkan nilai akhir: ";
            cin >> nilaiAkhir;
            vector<Mahasiswa*> hasil = hashTable.cariDataNilai(nilaiAwal, nilaiAkhir);
            if (!hasil.empty()) {
                cout << "Mahasiswa dengan nilai dalam rentang " << nilaiAwal << " - " << nilaiAkhir << ":" << endl;
                for (Mahasiswa* mahasiswa : hasil) {
                    cout << mahasiswa->nim << ", " << mahasiswa->nilai << endl;
                }
            } else {
                cout << "Tidak ada mahasiswa dengan nilai dalam rentang tersebut" << endl;
            }
        }
    }
    return 0;
}
```
#### Interpretasi 
Kode di atas merupakan kode yang menerangkan tentang struktur data Hash Table dengan alur program sebagai berikut :
- Pertama, kode membuat objek HashTable untuk menyimpan data siswa.
- kemudian membuat sebuah loop yang akan berjalan sampai user memilih untuk keluar.
- Selama loop, kode menampilkan menu dan meminta mereka untuk memilih salah satu opsi. Jika user  memilih opsi 1, kita akan meminta mereka untuk memasukkan NIM dan nilai, kemudian membuat objek 'mahasiswa' baru dan menambahkannya ke dalam hash table menggunakan fungsi tambahData. 
- Jika user memilih opsi 2, kita akan meminta mereka untuk memasukkan NIM dan nilai.
- Jika opsi 3, maka kode akan meminta user untuk memasukkan NIM yang akan dicari, kemudian kode akan menjalankan menggunakan fungsi 'cariDataNIM'. Jika ditemukan maka kode akan menampilkan informasi tentang mahasiswa.

Berikut fungsi dan komponen dari kode:
- Mahasiswa : kelas yang merepresentasikan data mahasiswa, yang terdiri dari atribut nim dan nilai.
- HashTable :  kelas yang menjelaskan hash table, yang terdiri dari atribut table yang merupakan yang menyimpan data mahasiswa.
- hashFunction : menghitung indeks hash dari sebuah NIM.
- tambahData : menambahkan data mahasiswa ke dalam hash table.
- hapusData : menghapus data mahasiswa dari hash table berdasarkan NIM.
- cariDataNIM : mencari data mahasiswa berdasarkan NIM.
- cariDataNilai : mencari data mahasiswa berdasarkan rentang nilai.

#### Output
![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/16063332-b674-4cfe-8217-a3ee87ff5618)
Pada kode di atas akan menampilkan sebuah output berupa tampialan output interaktif dengan empat menu pilihan yaitu Tambah data, hapus data, cari data berdasarkan NIM, serta cari data berdasarkan rentang nilai. Output ini bisa dipilih dengan interaktif sesuai input oleh user.

 ## Refrensi
 [1]V. Mutiawani, “HASHTABLE SEBAGAI ALTERNATIF DARI ALGORITMA PENCARIAN BINER PADA APLIKASI E-ACESIA,” Jurnal Informatika, vol. 8, no. 2, Jul. 2014, Accessed: Jun. 18, 2024. [Online]. Available: http://journal.uad.ac.id/index.php/JIFO/article/view/2060/1320

 [2]programiz, “Hash Table,” Programiz.com, 2019. https://www.programiz.com/dsa/hash-table

 [3]“Data Structure and Algorithms - Hash Table - Tutorialspoint,” Tutorialspoint.com, 2020. https://www.tutorialspoint.com/data_structures_algorithms/hash_data_structure.htm