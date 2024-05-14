# <h1 align="center">CPMK 2 - SubCPMK 7</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## CPMK 2 - SubCPMK 7
1. Tulislah sebuah program dari operasi queue seperti enqueue/add, dequeue/remove, isEmpty, isFull, dll(min 5)! (60 Poin)

#### Jawaban
``` C++
#include <iostream>

using namespace std;

class Antrian {
private:
    int item[5], depan, belakang;

public:
    Antrian() {
        depan = -1;
        belakang = -1;
    }

    // Memeriksa apakah antrian penuh
    bool penuh() {
        if (depan == 0 && belakang == 4) {
            return true;
        } else {
            return false;
        }
    }

    // Memeriksa apakah antrian kosong
    bool kosong() {
        if (depan == -1) {
            return true;
        } else {
            return false;
        }
    }

    // Menambahkan elemen ke antrian
    void tambah(int elemen) {
        if (penuh()) {
            cout << "Antrian penuh" << endl;
        } else {
            if (depan == -1) {
                depan = 0;
            }
            belakang++;
            item[belakang] = elemen;
            cout << endl << "Ditambahkan " << elemen << endl;
        }
    }

    // Menghapus elemen dari antrian
    int hapus() {
        int elemen;
        if (kosong()) {
            cout << "Antrian kosong" << endl;
            return (-1);
        } else {
            elemen = item[depan];
            if (depan >= belakang) {
                depan = -1;
                belakang = -1;
            } else {
                depan++;
            }
            cout << endl << "Dihapus -> " << elemen << endl;
            return (elemen);
        }
    }

    // Mencetak isi antrian
    void tampilkan() {
        if (kosong()) {
            cout << endl << "Antrian kosong" << endl;
        } else {
            cout << endl << "Indeks depan -> " << depan;
            cout << endl << "Item -> ";
            for (int i = depan; i <= belakang; i++) {
                cout << item[i] << " ";
            }
            cout << endl << "Indeks belakang -> " << belakang << endl;
        }
    }
};

int main() {
    Antrian a;

    a.tambah(1);
    a.tambah(3);
    a.tambah(5);
    a.tambah(7);
    a.tambah(9);

    a.tampilkan();

    a.hapus();

    a.tampilkan();

    return 0;
}
```

2. Sebuah selter hewan terlantar, yang mana hanya menerima kucing dan anjing, menerapkan konsep “first in, first out” dalam proses adopsi. Orang-orang yang hendak mengadopsi harus mengikuti aturan berikut:
 1) mengadopsi hewan yang paling “tua” (berdasarkan waktu masuk ke selter) dan tidak dapat memilih kucing atau anjing; 
 2) memilih antara kucing atau anjing, namun akan menerima yang paling tua. Buatlah data struktur untuk mengimplementasikan kondisi tersebut, silahkan menggunakan beberapa operasi queue seperti enquee, dequeueAny, dequeueDog, dan dequeueCat. (40 Poin)


#### Jawaban

``` C++
#include <iostream>
#include <queue>
#include <string>

using namespace std;


struct Animal {
    string type; 
    int arrivalTime; 

    
    Animal(string _type, int _arrivalTime) : type(_type), arrivalTime(_arrivalTime) {}
};

// Struktur untuk shelter
struct AnimalShelter {
    
    queue<Animal> catQueue; 
    
    queue<Animal> dogQueue; 
    
    int timeCounter; 

    // Konstruktor untuk inisialisasi shelter
    AnimalShelter() {
        timeCounter = 0; 
    }

    // Fungsi untuk mengadopsi hewan yang paling tua
    Animal dequeueAny() {
        
        if (catQueue.empty() && dogQueue.empty()) {
            cout << "Tidak ada hewan yang tersedia untuk diadopsi.\n";
            return Animal("", -1); 
        } else if (catQueue.empty()) {
            
            Animal oldestDog = dogQueue.front();
            dogQueue.pop();
            return oldestDog;
        } else if (dogQueue.empty()) {
           
            Animal oldestCat = catQueue.front();
            catQueue.pop();
            return oldestCat;
        } else {
            
            if (catQueue.front().arrivalTime < dogQueue.front().arrivalTime) {
                Animal oldestCat = catQueue.front();
                catQueue.pop();
                return oldestCat;
            } else {
                Animal oldestDog = dogQueue.front();
                dogQueue.pop();
                return oldestDog;
            }
        }
    }

    // Fungsi untuk mengadopsi kucing yang paling tua
    Animal dequeueCat() {
        
        if (catQueue.empty()) {
            cout << "Tidak ada kucing untuk diadopsi.\n";
            return Animal("", -1); 
        } else {
            
            Animal oldestCat = catQueue.front();
            catQueue.pop();
            return oldestCat;
        }
    }

    // Fungsi untuk mengadopsi anjing yang paling tua
    Animal dequeueDog() {
        
        if (dogQueue.empty()) {
            cout << "Tidak ada anjing untuk diadopsi.\n";
            return Animal("", -1); 
        } else {
            
            Animal oldestDog = dogQueue.front();
            dogQueue.pop();
            return oldestDog;
        }
    }

    // Fungsi untuk menambahkan hewan ke shelter
    void enqueue(string type) {
        
        if (type == "kucing") {
            catQueue.push(Animal(type, timeCounter++));
        } else if (type == "anjing") {
           
            dogQueue.push(Animal(type, timeCounter++));
        } else {
            
            cout << "Hewan yang tidak dikenal.\n";
        }
    }
};

int main() {
    // Membuat shelter
    AnimalShelter shelter;

    
    shelter.enqueue("kucing");
    shelter.enqueue("anjing");
    shelter.enqueue("kucing");
    shelter.enqueue("anjing");

    
    Animal adoptedAnimal = shelter.dequeueAny();
    cout << "Hewan yang diadopsi: " << adoptedAnimal.type << endl;

   
    Animal adoptedCat = shelter.dequeueCat();
    cout << "Kucing yang diadopsi: " << adoptedCat.type << endl;

    
    Animal adoptedDog = shelter.dequeueDog();
    cout << "Anjing yang diadopsi: " << adoptedDog.type << endl;

    return 0;
}
```