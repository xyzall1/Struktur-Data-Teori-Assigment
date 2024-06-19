# <h1 align="center">CPMK 2 - SubCPMK 4</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## CPMK 2 - SubCPMK 4
1. Berikan penjelasan dari struct dan buatlah sebuah contoh program dari struct! (100 poin)

#### Jawaban

1. Pengertian
Struct yaitu salah satu tipe data yang berisikan kumpulan variabel-variabel serta bernaung dalam satu nama yang sama serta memilki kaitan satu sama lain. Dalam struct kita dapat memilki variabel-variabel yang bertipe data yang sama atau berbeda, bahakan struct sendiri dengan menyimpan variabel yang bertipe data array atau struct itu sendiri.

2. Cara Menggunakan Struct
Penggunaan atau pemakaian tipe data struct dilakukan dengan membuat suatu variabel yang bertipe data struct tersebut. Pengaksesan elemen struct yang akan dilakukan secara individual dengan menyebutkan nama variabel struct diikuti dengan operator titik (.) Seperti pada kode di bawah ini :

3. Pengelompokan Data
Struct memungkinkan kita untuk mengelompokkan data terkait bersama-sama. Ini sangat berguna ketika memiliki sejumlah variabel yang saling terkait dan ingin memperlakukan mereka sebagai satu kesatuan. Misalnya, dalam pengelompokan mahaiswa di kelas, kita dapat menggunakan struct untuk menyimpan informasi seperti nama, NIM, umur, asal daerah dan informasi lainnya dalam satu unit.

4. Penggunaan Struct
Penggunaan struct memiliki beberapa pilihan untuk mendeklarasikan variabel ketika tipe struktur ditentukan dengan menempatkan satu atau lebih nama variabel yang dipisahkan koma di antara kurung kurawal penutup dan titik koma. Variabel struktur dapat diinisialisasi. Inisialisasi setiap variabel harus diapit kurung kurawal.

Berikut contoh programnya :
Menampilkan struktur buku dengan struct yang berupa array berukuran 5.

```C++
#include<iostream>

using namespace std;

struct buku{
    string judul_buku;
    string pengarang;
    string penerbit;
    int tebal_halaman;
    int harga_buku;
};buku data1[5];

int main(){

    data1[0].judul_buku = "Sebuah Seni Untuk Bersikap Bodo Amat";
    data1[1].judul_buku = "Sebuah Seni Untuk Bersikap Tidak Bodo Amat";
    data1[2].judul_buku = "1001 Cara Sukses di Usia Tua";
    data1[3].judul_buku = "3000 Cara Meningkatkan Kinerja Otak";
    data1[4].judul_buku = "Cara Menikmati Hidup Tanpa Beban";

    data1[0].pengarang = "Aurel Rowling";
    data1[1].pengarang = "Aliana Sawafi";
    data1[2].pengarang = "Rosa Nur";
    data1[3].pengarang = "Dewanti Angguna";
    data1[4].pengarang = "Laksita Ardelia";

    data1[0].penerbit = "Garam Media";
    data1[1].penerbit = "Gula Media";
    data1[2].penerbit = "Erlangga";
    data1[3].penerbit = "Garuda";
    data1[4].penerbit = "Empat Mata";

    data1[0].tebal_halaman = 233;
    data1[1].tebal_halaman = 290;
    data1[2].tebal_halaman = 157;
    data1[3].tebal_halaman = 480;
    data1[4].tebal_halaman = 670;

    data1[0].harga_buku = 600000;
    data1[1].harga_buku = 34000;
    data1[2].harga_buku = 459000;
    data1[3].harga_buku = 670000;
    data1[4].harga_buku = 870000;
    

    
    for(int i=0; i<5; i++){
    cout<<"Data Buku ke-"<<i+1<<endl;
    cout<<"Judul: "<<data1[i].judul_buku<<endl;
    cout<<"Pengarang: "<<data1[i].pengarang<<endl;
    cout<<"Penerbit: "<<data1[i].penerbit<<endl;
    cout<<"Tebal Halaman: "<<data1[i].tebal_halaman<<endl;
    cout<<"Harga: "<<data1[i].harga_buku<<endl;
    cout<<endl;
    cout<<endl;
    }
    return 0;
}

```
Kode di atas merupakan sebuah program yang akan menjalankan kode yang memuat tentang struct yang bernama 'buku' lalu memiliki lima variabel seperti (judul buku yang menyimpan string judul buku, pengarang akan menyimpan string nama pengarang buku, penerbit yang akan menyimpan nama penerbit buku, tebal halaman akan menyimpan integer jumlah tebal halaman buku, harga buku akan meyimpan harga beli buku). Kemudian pada array tersebut yang didefinisikan dengan 'data1' lalu dengan kapasitas 5 elemen yang nantinya elemen tersebut adalah sebuah objek dar struct 'buku'. Lalu kode tersebut menginisialisasi setiap elemen array dengan nilai-nilai yang telah ditentukan. Kemudian kode tersebut akan menggunakan perulangan 'for' lalu mencetak semua data yang telah disimpan pada setiap elemen dari array 'data1'. setelah itu kode akan mengakhiri program dengan mengembalikan nilai '0' dengan fungsi 'main'. Oleh karena itu kode akan menyimpan dan mencetak data-data tentang lima buku yang telah ditentukan. 

#### Output:
![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/c625985e-b3b4-430f-9ef9-8e35bc124179)

Saat dijalankan kode tersebut akan menampilkan sebuah output berupa data berupa buku yang di mana isinya berisikan variabel, di mana ada lima data buku dalam output yang akan dijalankan dalam kode serta dalam data buku tersebut terdapat lima variabel juga yaitu (judul, pengarang, penerbit, tebal halaman, serta harga buku). Data buku tersebut nantinya akan keluar sesuai terhadap masing-masing inputan array yang kita masukkan. Seperti gambar di atas ini.