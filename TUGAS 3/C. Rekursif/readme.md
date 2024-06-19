# <h1 align="center">Rekursif</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Penjelasan 
Fungsi rekursif merupakan fungsi yang mengacu pada dirinya sendiri dan terdiri dari dua bagian yaitu basis dan rekurens. Basis berisi nilai awal yang tidak mengacu pada dirinya sendiri dan berfungsi untuk memberikan nilai yang terdefinisi pada fungsi rekursif dan sekaligus menghentikan proses rekursi.Sedangkan rekurens adalah bagian fungsi yang mendefinisikan argumen fungsi dalam terminologinya sendiri, dan setiap kali fungsi tersebut melakukan bagean tertentu, fungsi tersebut disebut sebagai fungsi rekursif [1]. Kelebihan menggunakan fungsi rekursif adalah program menjadi lebih singkat. Ini juga membuat penggunaannya lebih mudah dalam beberapa situasi, seperti pangkat, factorial, dan fibonacci, serta beberapa proses deret lainnya. Fungsi rekursif juga lebih cepat dan efisien daripada proses iteratif. Fungsi rekursif memiliki kekurangan bahwa ia membutuhkan lebih banyak memori karena setiap bagian dari dirinya dipanggil membutuhkan ruang memori yang lebih besar untuk disimpan. Rekursif seringkali tidak bisa berhenti, menyebabkan memori terpakai habis dan program error [2] 


## Contoh Program 
```C++
#include<iostream>
using namespace std;

// Fungsi rekursif untuk menghitung nilai faktorial
long long faktorial(int n) {
  if(n == 0)
    return 1;
  else
    return n * faktorial(n-1);
}

int main() {
  int bilangan;
  
  // Meminta input bilangan bulat positif
  cout << "Masukkan bilangan bulat positif: ";
  cin >> bilangan;
  
  // Menghitung faktorial dari bilangan
  long long hasil = faktorial(bilangan);
  
  // Menampilkan hasil
  cout << "Faktorial dari " << bilangan << " adalah: " << hasil << endl;
  
  return 0;
}
```
#### Interpretasi
Kode di atas menggunakan struktur data rekursif dengan menerapkan menghitung bilangan faktorial. Berikut alur kode di atas:
- Pertama kita menggunakan cout untuk memasukkan bilangan positif.
- Kemudian, kode menggunakan perintah cin untuk membaca input user dan menyimpannya dalam variabel bilangan.
- Lalu kode memanggil fungsi faktorial dengan mengirimkan variabel bilangan sebagai argumen..
- Nilai faktorial dari bilangan tersebut akan dihitung oleh fungsi faktorial dengan menggunakan teknik rekursif.
- lalu kode menggunakan fungsi if dalam fungsi faktorial untuk mengetahui apakah bilangan sama dengan 0. Jika hasilnya adalah ya, maka kita mengembalikan nilai 1, karena faktorial dari 0 adalah 1.
- Jika ada bilangan yang tidak sama dengan 0, maka kode mengembalikan hasil perkalian antara bilangan tersebut dengan hasil panggilan fungsi faktorial dengan argumen n-1. Ini adalah contoh rekursi karena fungsi faktorial memanggil dirinya sendiri dengan argumen yang berbeda.
- Setelah fungsi faktorial dijalankan, hasil faktorial diambil dari angka dan disimpan dalam variabel hasil.
- Terakhir, kode menggunakan perintah cout untuk menampilkan hasil faktorial.

Berikut fungsi & komponen yang digunakan:
- faktorial : fungsi rekursif yang berfungsi untuk menghitung nilai faktorial dari sebuah bilangan.
- main : fungsi yang digunakan untuk menjalankan sistem operasional program.

#### Output:
![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/885fb8c9-cfa2-4f51-85c4-e133b2ed0f5a)

Saat kode dijalankan kode ini menggunakan rekursif langsung, dengan fungsi factorial(n) untuk menghitung faktorial dari bilangan n dengan mengembalikan n dengan faktorial dari n-1. Fungsi ini akan meminta input oleh user dari sebuah bilangan positif oleh user, menghitung faktorialnya, serta menampilkan hasilnya. Di sini user memasukkan angka bilangan positif 5 dan prosesnyya 5 * 4 * 3 * 2 * 1 yang hasiknya yaitu 120.


 ## Refrensi
 [1]S. Herlambang, “Implementasi Fungsi Rekursif Dalam Algoritma dan Perbandingannya dengan Fungsi Iteratif.” Available: https://informatika.stei.itb.ac.id/~rinaldi.munir/Matdis/2008-2009/Makalah2008/Makalah0809-079.pdf


 [2]“PRAKTIKUM 7 REKURSIF S1 IF 11.” Accessed: Jun. 18, 2024. [Online]. Available: https://yuliana.lecturer.pens.ac.id/Struktur%20Data/PRAKTIKUM%202015/Praktikum%207%20-%20Rekursif%201.pdf

 [3]“Struktur Data Queue: Pengertian, Jenis, dan Kegunaannya,” Trivusi, Sep. 16, 2022. https://www.trivusi.web.id/2022/07/struktur-data-queue.html