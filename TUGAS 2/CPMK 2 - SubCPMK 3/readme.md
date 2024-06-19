# <h1 align="center">CPMK 2 - SubCPMK 3</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## CPMK 2 - SubCPMK 3
1. Terdapat dua algoritma searching yang umum digunakan yakni, Binary Search dan Linear Search. Berikan penjelasan alur dari masing-masing algoritma tersebut, dan jelaskan runtime dari best case dan worst case masing-masing algoritma! (35 Poin)

#### Jawaban
 A. Binary Search
- Berikut alur dari algoritma Binary Search :
    - Pertama buat perulangan lalu menentukan posisi low yaitu posisi yang menandakan index paling rendah kemudian menentukan posisi high. Kemudian mencari posisi mid = (high + low)/2.
    - Kemudian kita bandingkan data yang dicari dengan nilai yang ada di posisi mid.
    - Jika data yang dicari sama dengan nilai yang ada di posisi mid berarti data ditemukan.
    - Namun jika data yang dicari lebih kecil dari nilai yang ada di posisi mid maka pencarian data akan dilakukan di bagian kiri mid dengan melakukan pembandingan dengan kondisi posisi high berubah yaitu (mid - 1) serta posisi low tetap.
    - Selanjutnya jika data yang dicari lebih besar maka nilai yang ada di mid pencarian data akan dilakukan di bagian kanan dari mid dengan posisi low yang berubah yaitu (mid + 1).

- Runtime dari best case dan worst case 
Jika kita melihat dari alur algoritma di atas, proses dari Binary search untuk runtime best case yaitu O(1) hal ini akan terjadi jika elemen yang dicari adalah elemen yang pertama dalam array namun runtime akan menjadi worst case jika O(log n) jika elemen yang dicari yaitu elemen terakhir dalam array.

B. Linear Search
- Berikut alur dari algoritma Linear Search:
    - Kita mulai dari indeks ke-0 dari beberapa larik masuka, lalu akan kita bandingkan nilai kunci dengan nilai yang ada di indeks ke-0
    - kemudian jika nilainya cocok dengan kuncinya, maka kembalikan posisi di mana nilai itu ditemukan.
    - Lalu jika nilainya tidak cocok maka bandingkan elemen berikut dalam array.
    - Selanjutnya ulangi langkah yang ketiga hingga ditemukan yang cocok, lalu kembalikan posisi di mana kecocokan ditemukan.
    - Selanjutnya yang terakhir jika pencarian tidak berhasil maka cetak bahwa elemen tersebut tidak ada dalam array hingga keluar dari program.

- Runtime dari best case dan worst case 
Jika kita melihat dari alur algoritma di atas, proses dari Linear search memiliki best case yaitu O(1) karena ketika elemen yang akan dicari akan lebih cepat jika elemen pertama dalam array sedangkan kondisi worst case runtime berupa O(n) dikarenakan elemen yang dicari yaitu elemen terakhir dalam array.

2. Buatlah fungsi dari salah satu algoritma searching pada soal nomor 1, dan berikan penjelasan pada program tersebut (35 Poin).

#### Jawaban

```C++
#include <iostream>
using namespace std;

// Fungsi binary search
void binarySearch(int arr[], int n, int target) {
    int left = 0; 
    int right = n - 1; 

    while (left <= right) {
        int mid = left + (right - left) / 2; 

        // Jika target ditemukan, kode cetak indeks
        if (arr[mid] == target) {
            cout << "Elemen berada pada index ke- " << mid << endl;
            return;
        }

        // Jika target lebih kecil dari elemen tengah, buang kanan
        if (arr[mid] > target) {
            right = mid - 1;
        }

        // Jika target lebih besar dari elemen tengah, buang kiri
        else {
            left = mid + 1;
        }
    }

    
    cout << "Elemen tidak termasuk anggota array" << endl;
}

int main() {
    int arr[] = {1, 3, 5, 7, 9, 11, 13, 15};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target;

    cout << "Input Elemen: ";
    cin >> target;

    binarySearch(arr, n, target);

    return 0;
}

```
### Interpretasi 
Kode tersebut menggunakan metode binary search. 
- Menggunakan tiga parameter yaitu arr[] yang akan diacri array nya, n untuk jumlah elemen, serta target untuk elemen yang dicari.
- Deklarasi terdapat dua jumlahnya yaitu menggunakan variabel left dan right sebgai index kiri dan kanan dari array. Lalu menginisialisasi left dengan 0 serta right dengan n-1 atau indeks terakhir array.
- Selanjutnya akan dilakukan perulangan while hingga left lebih kecil atau sama dengan right. Kode akan menjalankan setiap perulangan kode akan menghitung mid dari array.
- Jika elemen di index tengah sama dengan target, maka elemen ditemukan dengan index mid. Kemudian kode akan keluar serta mencetak fungsi menggunakan perintah return. Jika target lebih kecil pada index tengah maka akandigeser ke kanan serta menjadi mid - 1 atau index akan dikurangi -1 lalu akan memfokuskan pencarian pada bagian kiri dari array.
- Namun jika lebih besar, maka elemen index tengah akan menggeser ke kiri serta menjadi mid +1 atau index ke kiri untuk memfokuskan pencarian pada bagian kanan array.
- Jika perulangan while selesai dan target ditemukan maka kode akan mencetak pesan elemen tidak termasuk anggota dari array.
- Pada fungsi main kita akan enambah array dengan 8 elemen serta mendeklrasikan dengan n untuk jumlah elemen dari array. Kemudia kode akan memerintah user untuk input array random.
- Jika inputan yang dimasukkan bukan merupakan anggota elemen maka kode akan mencetak pesan "Elemen tidak termasuk anggita array" begitupun sebaliknya jika inputan yang dimasukkan merupakan salah satu anggota dari array.  


3. Tulislah sebuah fungsi program dengan kondisi sebagai berikut:
Terdapat sebuah sorted array of strings yang mana terdapat string kosong diantaranya, carilah lokasi/indeks dari kata yang dicari! (30 Poin)
Input: bola, {“Adi”,””,””, “”, “bermain”, “”, “bola”, “”, “”, “sedang”}
Output: 6


#### Jawaban 
``` C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// Fungsi binary search untuk mencari index string di array
int findIndex(vector<string>& arr, string target) {
    // tambah variabel untuk menentukan batas kiri dan kanan array
    int left = 0; 
    int right = arr.size() - 1; 

    //Perulangan proses pencarian
    while (left <= right) {
        int mid = left + (right - left) / 2; 

        while (arr[mid] == "" && mid >= left)
            mid--;

        if (mid < left)
            left = left + 1;
        else if (arr[mid] == target)
            return mid;
        else if (arr[mid] > target)
            right = mid - 1;
        else
            left = mid + 1;
    }

    return -1;
}

int main() {
    vector<string> arr = {"Adi", "", "", "", "bermain", "", "bola", "", "", "sedang"}; 
    string target = "bola"; 

    //Mencari index string dalam array
    int resultIndex = findIndex(arr, target);

    //Mencetak pesan untuk user
    if (resultIndex != -1) {
        cout << "Output: " << resultIndex << endl;
    } else {
        cout << "Kata \"" << target << "\" tidak ditemukan dalam array" << endl;
    }

    return 0;
}
```


