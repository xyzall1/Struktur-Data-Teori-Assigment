# <h1 align="center">CPMK 2 - SubCPMK 2</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## CPMK 2 - SubCPMK 2
1. Terdapat tiga algoritma sorting yang umum digunakan yakni, Bubble Sort, Selection Sort, dan Merge Sort. Berikan penjelasan alur dari masing-masing algoritma tersebut, dan jelaskan runtime dari best case dan worst case masing-masing algoritma! (35 Poin)

#### Jawaban
1. Bubble Sort
- Berikut alur dari algoritma bubble sort:
    - Kita membandingkan nilai data ke-1 lalu data ke-2.
    - Kemudian data ke-1 jika lebih besar dari data ke-2 maka akan kita tukar posisinya.
    - Selanjutnya jika ada data yang lebih besar tadi maka bandingkan dengan data ke-3.
    - Lalu lakukanlah langkah yang kedua hingga selesai.

- Runtime dari best case dan worst case 
Jika kita melihat dari alur algoritma di atas, proses dari bubble sort sendiri akan bekerja secara berulang-ulang hingga array nantinya urut. Bubble sort sendiri memiliki best case O(n) serta worst case dengan O(n^2). Jika pada kasus ini array belum terurut maka algoritma akan diperintah untuk mengurutkan terlebih dahulu, serta algoritma akan membandingkan satu per satu terlebih dahulu jadi akan memakan banyak waktu. 

2. Selection Sort
- Berikut alur dari algoritma Selection sort:
    - Kita cari elemen dengan nilai terkecil jika yang diminta dengan metode ascending dan begitupun sebaliknya dari yang terbesar maka descending.
    - Jika sudah menemukan maka jadikan elemen tersebut di urutan yang pertama.
    - Lakukan langkah-langkah di atas sehingga, selection sort ini akan mengulangi hal yang sama, dengan mencari nilai terbesar atau terkecil dari array.
    - Proses akan dilakukan berulang sampai dengan semua elemen array berhasil kita sorting.

- Runtime dari best case dan worst case 
Jika kita melihat dari alur algoritma di atas, proses dari selection sort maka best case dan worst case sort ini yaitu sama-sama O(n^2). Hal ini tidak berbeda karena algoritma ini tidak memiliki penyesuaian untuk array yang sudah urut.

3. Merge Sort 
- Berikut alur dari algoritma Merge sort:
    - Jumlah elemen array dibagi menjadi dua mid = n/2.
    - Selanjutnya elemen array kiri dibagi menjadi dua serta elemen kana dibagi dua.
    - Kita lakukan lagi langkah yang kedua dengan masing-masing dibagi dua.
    - Kemudian untuk setiap elemen akan dilakukan perbandingan, jika elemen array sebelah kanan lebih kecil dari isi array maka sebelah kiri ditukar.
    - Berikutnya yaitu kita lakukan langkah pengurutan serta penggabungan array seperti tahap sebelumnya.

- Runtime dari best case dan worst case 
Jika kita melihat dari alur algoritma di atas yaitu O(n log n). Waktu eksekudi yang terbaik jika pada algoritma ini didapatkan dapat dibagi dengan sama namun sebaliknya jika array yang didapatkan akan susah dibagi dengan sama maka akan menjadi waktu eksekusi yang terburuk.

Berikut tabel dari Best Case, Average Case, dan Worst Case dari masing-masing metode sort.

![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/15f1c902-1085-4892-9ee1-5d2f7d493593)


2. Buatlah fungsi dari salah satu algoritma sorting pada soal nomor 1, dan berikan penjelasan pada program tersebut (35 poin)

#### Jawaban

```C++
#include <iostream>
using namespace std;

// fungsi untuk mengurutkan array dari tipe float menggunakan algoritma Selection Sort
void selectionSort(float arr[], int n) {
    // iterasi melalui array, mulai dari elemen yang pertama
    for (int i = 0; i < n-1; i++) {
        // asumsikan bahwa nilai minimum adalah elemen pertama dari bagian yang belum disortir
        int minIndex = i;
        // iterasi 
        for (int j = i+1; j < n; j++) {
            // kalau elemen saat ini lebih besar dari elemen berikutnya
            if (arr[j] > arr[minIndex]) {
                // perbarui indeks minimum jadi indeks dari elemen yang lebih besar
                minIndex = j;
            }
        }
        // tukar nilai minimum yang ada di bagian belum disortir dengan elemen pertama dari bagian belum disortir
        swap(arr[minIndex], arr[i]);
    }
    // print keterangan
    cout << "URUTAN IPS MAHASISWA DARI TERBESAR HINGGA TERKECIL" << endl;
    cout << "==================================================" << endl;
    for (int i = 0; i < n; i++) {
        cout << "IPS " << i+1 << " : " << arr[i] << endl;
    }
}

int main() {
    // menjelaskan array menggunakan float
    float IPS[5] = {3.8, 2.9, 3.3, 4.0, 2.4};
    // hitung ukuran dari array
    int size = sizeof(IPS)/sizeof(IPS[0]);
    // panggil fungsi selectionSort untuk mengurutkan array secara menurun
    selectionSort(IPS, size);
    // return 0 jika program berhasil 
     return 0;
}

```
### Interpretasi 
Kode di atas merupakan sebuah program yang akan menjalankan kode sorting dengan metode Selection Sort. Seperti biasanya kita menggunakan <iostream> sebelum memulai kode cpp. Kita awali dengan membuat fungsi void yang merupakan fungsi yang digunakan untuk melakukan kode tanpa mengembalikan nilai.

Pada kode ini '(int i = 0; i < n-1; i++)' kita akan melakukan iterasi melalui array, mulai dari elemen yang pertama, kemudian kita akan asumsikan nilai yang terkecil pada elemen pertama sebelum disortir menggunakan kode 'int minIndex = i; dan for (int j = i+1; j < n; j++)', berikutnya kita akan sortir dengan metode selection sort dengan catatan jika elemen saat ini lebih besar dari elemen berikutnya maka tukar dengan perintah kode  if 'arr[j] > arr[minIndex]' 'minIndex = ' 'swap arr[minIndex], arr[i]' selanjutnya kita akan menambahkan keterangan opsional dengan kode 'cout << "URUTAN IPS MAHASISWA DARI TERBESAR HINGGA TERKECIL" << endl;' Selanjutnya kita akan mencetak output dengan menggunakan kode ini 'for (int i = 0; i < n; i++) cout << "IPS " << i+1 << " : " << arr[i] << endl'

Tidak lupa kita juga akan memberi inputan IPS yang akan dijalankan dengan data yang bertipe float float IPS[5] = {3.8, 2.9, 3.3, 4.0, 2.4}; yang berjumlah lima elemen atau [5] selanjutnya kita akan melakukan perhitungan untuk mengurutkan array dengan metode pembagian lalu kita panggil array yang sudah dipanggil dengan kode 'selectionSort(IPS, size)' serta yang terakhir jangan lupa untuk mengetikkan 'return 0' jika kode berhasil.

#### Output:
![Cuplikan layar 2024-04-01 070715](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/c07b7f3c-4f42-4ef3-9dd6-5d4978e587db)
Saat dijalankan kode trsebut langsung akan menampilkan data IPS Mahasiswa dari terbesar hingga terkecil sesuai dengan kode dan soal yang diberikan. Output akan menjelaaskan bahwasannya tingkat IPS 1 atau IPS yang tertinggi yaitu 4, lalu dilanjutkan IPS 2 dengan 3.8 dan seterusnya hingga IPS yang paling kecil yaitu IPS 5 dengan 2,4.

Kompleksitas waktu dari kode tersebut yaitu O(n^2), singkat saya jelaskan di mana n yaitu ukuran dari array. Dikarenakan adanya perulangan for di dalam fungsi 'selectionSort' yang memiliki kompleksitas waktu O(n) sendiri-sendiri atau O(n) x O(n) lalu totalnya O(n^2).
Untuk kompleksitas ruang sendiri yaitu O(1) karena penggunaan ruang tidak bergantung terhadap ukuran array, hal ini disebabkan penggunaan variabel lokal dan fungsi yang tak menggunakan variabel global sehingga jumlah memori yang dibutuhkan tak akan bertambah bila array bertambah besar.

3. Tulislah sebuah fungsi untuk mensorting dan mengecek dua buah array of strings, sehingga menghasilkan “anagram” dan “tidak anagram” (30 poin)
contoh
Input string1 = “bahu” string2 = “buah”
Output: “anagram”
Input string1 = “makan” string2 = “minum”
Output: “tidak anagram”

#### Jawaban 
``` C++
#include <iostream> 
#include <algorithm> 
#include <string> 
#include <vector> 

using namespace std; 

// Fungsi untuk memeriksa apakah dua string merupakan anagram
bool isAnagram(const string& str1, const string& str2) {
    vector<int> count(256, 0); // Inisialisasi vektor untuk menghitung jumlah karakter

    // Menghitung jumlah karakter pada string str1
    for (char c : str1) {
        count[c]++;
    }

    // Mengurangi jumlah karakter pada string str2
    for (char c : str2) {
        count[c]--;
    }

    // Memeriksa apakah ada karakter yang tersisa
    for (int count_val : count) {
        if (count_val != 0) {
            return false;
        }
    }

    return true; // Jika tidak ada karakter tersisa, maka string adalah anagram
}

// Fungsi untuk memeriksa apakah dua string merupakan anagram
string checkAnagram(const string& string1, const string& string2) {
    if (isAnagram(string1, string2)) {
        return "anagram"; // Jika string adalah anagram, maka kembalikan "anagram"
    } else {
        return "tidak anagram"; // Jika string tidak anagram, maka kembalikan "tidak anagram"
    }
}

int main() {
    string string1, string2; // Deklarasi string untuk menyimpan input user

    cout << "Masukkan string pertama: ";
    cin >> string1; 

    cout << "Masukkan string kedua: ";
    cin >> string2; 

    string result = checkAnagram(string1, string2); 
    cout << "Output: " << result << endl; 

    return 0;
}
```


4. Tulislah sebuah fungsi program dengan asumsi sebagai berikut:
Terdapat dua buah sorted array A dan B yang memiliki tipe data sama, dimana array A memiliki indeks yang cukup untuk menampung array B. Gabungkan array B kedalam array A, kemudian urutkan array tersebut! (30 Poin)


#### Jawaban

``` C++
#include <iostream>
#include <algorithm>

using namespace std;

void mergeArrays(int A[], int m, int B[], int n) {
    // Create a new array to store the merged array
    int mergedArray[m + n];
    int i = 0, j = 0, k = 0;

    // Merge the two arrays
    while (i < m && j < n) {
        if (A[i] <= B[j]) {
            mergedArray[k++] = A[i++];
        } else {
            mergedArray[k++] = B[j++];
        }
    }

    // Copy the remaining elements
    while (i < m) {
        mergedArray[k++] = A[i++];
    }
    while (j < n) {
        mergedArray[k++] = B[j++];
    }

    // Sort the merged array
    sort(mergedArray, mergedArray + m + n);

    // Copy the sorted array back to array A
    for (int i = 0; i < m + n; i++) {
        A[i] = mergedArray[i];
    }
}

int main() {
    int A[10] = {1, 4, 2, 3, 7};
    int B[] = {6, 3, 9, 7, 6};
    int m = 5, n = 5;

    mergeArrays(A, m, B, n);

    cout << "Array yang digabungkan dan diurutkan: " << endl;
    for (int i = 0; i < m + n; i++) {
        cout << A[i] << " ";
    }
    cout << endl;

    return 0;
}
```

   


    