# <h1 align="center">TUGAS 1</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

``` C++
#include <iostream>
using namespace std;

bool cekDuplikat(const int arr[], int panjangArr) {
    for(int i = 0, j = i + 1; i, j< panjangArr ; ++i, ++j) {
		 {
            if(arr[i] == arr[j]) {
                return true;
            }
        }
    }
    return false;
}

int main(void) {
    int arrA[] = {2, 1, 3, 1};
   int panjangArr = sizeof(arrA) / sizeof(arrA[0]);
   cout << (cekDuplikat(arrA, panjangArr) ? "Terdapat Duplikat" : "Tidak Terdapat Duplikat");
    //cout << cekDuplicat(arrA);
    return 0;
}
```