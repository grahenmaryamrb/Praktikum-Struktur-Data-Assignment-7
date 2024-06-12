# <h1 align="center">Laporan Praktikum Modul Stack & Queue</h1>
<p align="center">Grahen Maryam Rompas Basiran</p>
<p align="center">2311110055</p>

## Dasar Teori
### STACK
Dalam pemrograman, tumpukan, juga dikenal sebagai tumpukan, adalah komponen data yang penting. Dengan metode pemrosesan LIFO (Last In First Out), benda atau objek yang terakhir masuk ke dalam tumpukan akan menjadi benda pertama yang dikeluarkan dari tumpukan. Dengan model ini, hanya bagian paling atas (TOP) dari tumpukan yang dapat diakses. Bahwa struktur data dapat diterapkan pada array dan daftar terhubung adalah salah satu keuntungan stack [1].
![Screenshot]

### QUEUE
Antrian, juga dikenal sebagai antrian, adalah jenis struktur data yang dapat diproses dengan sifat FIFO, yang berarti elemen yang pertama kali masuk ke antrian akan keluar pertama. Dalam antrian, Anda dapat memasukkan elemen baru ke dalamnya atau mengeluarkannya. Ada dua jenis array linier dan sirkular yang dapat digunakan untuk membuat antena [2].

## Guided
### 1. PROGRAM STACK
```C++
#include <iostream>
using namespace std;

string arrayBuku[5];
int maksimal = 5, top = 0;

bool isFull() {
    return (top == maksimal);
}

bool isEmpty() {
    return (top == 0);
}

void pushArrayBuku(string data) {
    if (isFull()) {
        cout << "Data telah penuh" << endl;
    } else {
        arrayBuku[top] = data;
        top++;
    }
}

void popArrayBuku() {
    if (isEmpty()) {
        cout << "Tidak ada data yang dihapus" << endl;
    } else {
        arrayBuku[top - 1] = "";
        top--;
    }
}

void peekArrayBuku(int posisi) {
    if (isEmpty()) {
        cout << "Tidak ada data yang bisa dilihat" << endl;
    } else {
        int index = top;
        for (int i = 1; i <= posisi; i++) {
            index--;
        }
        cout << "Posisi ke " << posisi << " adalah " << arrayBuku[index] << endl;
    }
}

int countStack() {
    return top;
}

void changeArrayBuku(int posisi, string data) {
    if (posisi > top) {
        cout << "Posisi melebihi data yang ada" << endl;
    } else {
        int index = top;
        for (int i = 1; i <= posisi; i++) {
            index--;
        }
        arrayBuku[index] = data;
    }
}

void destroyArraybuku() {
    for (int i = top; i >= 0; i--) {
        arrayBuku[i] = "";
    }
    top = 0;
}

void cetakArrayBuku() {
    if (isEmpty()) {
        cout << "Tidak ada data yang dicetak" << endl;
    } else {
        for (int i = top - 1; i >= 0; i--) {
            cout << arrayBuku[i] << endl;
        }
    }
}

int main() {
    pushArrayBuku("Kalkulus");
    pushArrayBuku("Struktur Data");
    pushArrayBuku("Matematika Diskrit");
    pushArrayBuku("Dasar Multimedia");
    pushArrayBuku("Inggris");

    cetakArrayBuku();
    cout << "\n";
    cout << "Apakah data stack penuh? " << isFull() << endl;
    cout << "Apakah data stack kosong? " << isEmpty() << endl;
    peekArrayBuku(2);
    popArrayBuku();
    cout << "Banyaknya data = " << countStack() << endl;
    changeArrayBuku(2, "Bahasa Jerman");
    cout << endl;
    cetakArrayBuku();
    cout << "\n";
    destroyArraybuku();
    cout << "Jumlah data setelah dihapus: " << top << endl;
    cetakArrayBuku();

    return 0;
}
```
### Penjelasan
Program ini merupakan implementasi struktur data stack yang digunakan untuk menyimpan data buku. Diawali dengan mengimpor library iostream untuk memfasilitasi input/output.

Dideklarasikan array string dengan nama arrayBuku dan kapasitas 5 elemen untuk menyimpan elemen-elemen stack. Variabel maksimal diinisialisasi dengan nilai 5 untuk mewakili kapasitas maksimum stack, dan variabel top diinisialisasi dengan 0 sebagai pointer yang menunjuk ke elemen teratas di stack.

Beberapa fungsi disediakan untuk melakukan operasi-operasi pada stack, seperti isFull untuk mengecek apakah stack penuh, isEmpty untuk mengecek apakah stack kosong, pushArrayBuku untuk menambahkan elemen baru ke stack, popArrayBuku untuk menghapus elemen teratas, peekArrayBuku untuk melihat elemen pada posisi tertentu dari atas, countStack untuk mendapatkan jumlah elemen di dalam stack, changeArrayBuku untuk mengubah elemen pada posisi tertentu, destroyArrayBuku untuk menghapus semua elemen, dan cetakArrayBuku untuk mencetak semua elemen stack dari atas ke bawah.

Pada fungsi utama main, fungsi-fungsi operasi stack tersebut diuji dengan menambahkan beberapa buku ke stack, mencetak isinya, mengecek apakah penuh atau kosong, menampilkan data pada posisi tertentu, menghapus satu elemen, mengubah data pada posisi tertentu, mencetak ulang, menghapus semua data, dan mencetak ulang setelah penghapusan.

### PROGRAM QUEUE
```C++
#include <iostream>
using namespace std;

const int maksimalQueue = 5; // Maksimal antrian
int front = 0; // Penanda depan antrian
int back = 0; // Penanda belakang antrian
string queueTeller[5]; // Array untuk menyimpan antrian

bool isFull() { // Pengecekan antrian penuh atau tidak
    if (back == maksimalQueue) {
        return true; // =1
    } else {
        return false;
    }
}

bool isEmpty() { // Antrian kosong atau tidak
    if (back == 0) {
        return true;
    } else {
        return false;
    }
}

void enqueueAntrian(string data) { // Menambahkan antrian
    if (isFull()) {
        cout << "Antrian penuh" << endl;
    } else {
        if (isEmpty()) { // Jika antrian kosong
            queueTeller[0] = data;
            front++;
            back++;
        } else { // Jika antrian ada isi
            queueTeller[back] = data;
            back++;
        }
    }
}

void dequeueAntrian() { // Mengurangi antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = queueTeller[i + 1];
        }
        back--;
    }
}

int countQueue() { // Menghitung jumlah antrian
    return back;
}

void clearQueue() { // Menghapus semua antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = "";
        }
        back = 0;
        front = 0;
    }
}

void viewQueue() { // Melihat isi antrian
    cout << "Data antrian teller:" << endl;
    for (int i = 0; i < maksimalQueue; i++) {
        if (queueTeller[i] != "") {
            cout << i + 1 << ". " << queueTeller[i] << endl;
        } else {
            cout << i + 1 << ". (kosong)" << endl;
        }
    }
}

int main() {
    enqueueAntrian("Andi");
    enqueueAntrian("Maya");
    viewQueue();
    cout << "Jumlah antrian = " << countQueue() << endl;
    dequeueAntrian();
    viewQueue();
    cout << "Jumlah antrian = " << countQueue() << endl;
    clearQueue();
    viewQueue();
    cout << "Jumlah antrian = " << countQueue() << endl;
    return 0;
}
```
### PENJELASAN
Program diatas merupakan implementasi struktur data queue (antrian) yang mengikuti prinsip FIFO (First In, First Out), di mana elemen yang pertama masuk akan menjadi elemen yang pertama keluar. Diawali dengan mengimpor library iostream untuk memfasilitasi input/output.

Dideklarasikan konstanta maksimalQueue dengan nilai 5 yang mewakili kapasitas maksimum antrian. Variabel front diinisialisasi dengan 0 sebagai pointer yang menunjuk ke elemen terdepan, dan variabel back diinisialisasi dengan 0 sebagai pointer yang menunjuk ke elemen terbelakang dalam antrian. Didefinisikan array string queueTeller dengan kapasitas 5 elemen untuk menyimpan elemen-elemen antrian.

Beberapa fungsi disediakan untuk melakukan operasi-operasi pada antrian, seperti isFull untuk mengecek apakah antrian penuh, isEmpty untuk mengecek apakah antrian kosong, enqueueAntrian untuk menambahkan elemen baru ke antrian, dequeueAntrian untuk menghapus elemen terdepan, countQueue untuk mendapatkan jumlah elemen dalam antrian, clearQueue untuk menghapus semua elemen, dan viewQueue untuk mencetak semua elemen antrian.

Pada fungsi utama main, fungsi-fungsi operasi antrian tersebut diuji dengan menambahkan beberapa elemen ke antrian, mencetak isinya, mengecek apakah penuh atau kosong, menghapus elemen terdepan, menghitung jumlah elemen, menghapus semua elemen, dan mencetak ulang setelah penghapusan.

## Unguided
### 1. Buatlah program untuk menentukan apakah kalimat tersebut yang diinputkan dalam program stack adalah palindrom/tidak. Palindrom kalimat yang dibaca dari depan dan belakang sama. Jelaskan bagaimana cara kerja programnya.
```C++
#include <iostream>
#include <string>

using namespace std;

bool isPalindrome(string kalimat) {
    int awal = 0;
    int akhir = kalimat.length() - 1;

    while (awal < akhir) {
        if (kalimat[awal] != kalimat[akhir]) {
            return false;
        }
        awal++;
        akhir--;
    }
    return true;
}

int main() {
    string kalimat;
    cout << "Masukkan kalimat: ";
    getline(cin, kalimat);

    if (isPalindrome(kalimat)) {
        cout << "Kalimat tersebut adalah palindrom." << endl;
    } else {
        cout << "Kalimat tersebut bukan palindrom." << endl;
    }

    return 0;
}
```
#### Output:
![Screenshot]
### Penjelasan
Program diatas digunakan untuk menentukan apakah sebuah kalimat yang dimasukkan oleh pengguna merupakan palindrom atau bukan. Palindrom adalah kalimat yang jika dibaca dari depan dan belakang memiliki susunan karakter yang sama.

Diawali dengan mengimpor library iostream untuk memfasilitasi input/output dan library string untuk menggunakan tipe data string. Terdapat sebuah fungsi isPalindrome bertipe boolean yang menerima parameter kalimat bertipe string. Fungsi ini menginisialisasi dua variabel awal dan akhir untuk melacak indeks karakter dari awal dan akhir kalimat.

Dalam sebuah perulangan while, karakter pada posisi awal dibandingkan dengan karakter pada posisi akhir. Jika terdapat perbedaan, fungsi akan mengembalikan nilai false yang berarti kalimat tersebut bukan palindrom. Jika semua pasangan karakter sesuai, awal dan akhir akan semakin mendekati tengah kalimat, dan fungsi akan mengembalikan true jika tidak ditemukan ketidakcocokan.

Pada fungsi utama main, program meminta pengguna untuk memasukkan sebuah kalimat menggunakan getline. Kalimat yang diinputkan kemudian diperiksa apakah palindrom atau tidak dengan memanggil fungsi isPalindrome. Berdasarkan hasil dari fungsi tersebut, program akan mencetak apakah kalimat yang dimasukkan adalah palindrom atau bukan.

### 2. Ubah guided queue diatas agar menjadi program inputan user dan program menu
```C++
#include <iostream>
using namespace std;

const int maksimalQueue = 5; 
int front = 0; 
int back = 0; 
string queueTeller[5];

bool isFull() { // Pengecekan antrian penuh atau tidak
    return back == maksimalQueue;
}

bool isEmpty() { // Antrian kosong atau tidak
    return back == 0;
}

void enqueueAntrian(string data) { // Menambahkan antrian
    if (isFull()) {
        cout << "Antrian penuh" << endl;
    } else {
        queueTeller[back] = data;
        back++;
    }
}

void dequeueAntrian() { // Mengurangi antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back - 1; i++) {
            queueTeller[i] = queueTeller[i + 1];
        }
        queueTeller[back - 1] = "";
        back--;
    }
}

int countQueue() { // Menghitung jumlah antrian
    return back;
}

void clearQueue() { // Menghapus semua antrian
    if (isEmpty()) {
        cout << "Antrian kosong" << endl;
    } else {
        for (int i = 0; i < back; i++) {
            queueTeller[i] = "";
        }
        back = 0;
        front = 0;
    }
}

void viewQueue() { // Melihat isi antrian
    cout << "Data antrian teller:" << endl;
    for (int i = 0; i < maksimalQueue; i++) {
        if (queueTeller[i] != "") {
            cout << i + 1 << ". " << queueTeller[i] << endl;
        } else {
            cout << i + 1 << ". (kosong)" << endl;
        }
    }
}

void displayMenu() {
    cout << "Menu:" << endl;
    cout << "1. Tambah Antrian" << endl;
    cout << "2. Hapus Antrian" << endl;
    cout << "3. Lihat Antrian" << endl;
    cout << "4. Jumlah Antrian" << endl;
    cout << "5. Hapus Semua Antrian" << endl;
    cout << "6. Keluar" << endl;
    cout << "Pilih menu: ";
}

int main() {
    int choice;
    string data;

    do {
        displayMenu();
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Masukkan nama: ";
                cin >> data;
                enqueueAntrian(data);
                break;
            case 2:
                dequeueAntrian();
                break;
            case 3:
                viewQueue();
                break;
            case 4:
                cout << "Jumlah antrian = " << countQueue() << endl;
                break;
            case 5:
                clearQueue();
                break;
            case 6:
                cout << "Keluar dari program." << endl;
                break;
            default:
                cout << "Pilihan tidak valid." << endl;
        }
        cout << endl; // Untuk membuat jarak antara iterasi menu
    } while (choice != 6);

    return 0;
}
```
#### Output:
![Screenshot]
### Penjelasan
Program diatas merupakan implementasi struktur data queue (antrian) yang mengikuti prinsip FIFO (First In First Out). Program menyediakan beberapa operasi dasar pada antrian seperti menambahkan elemen (enqueue), menghapus elemen (dequeue), melihat isi antrian, menghitung jumlah elemen, mengosongkan antrian, serta menampilkan menu pilihan untuk interaksi pengguna.

Diawali dengan mengimpor library iostream untuk memfasilitasi input/output. Dideklarasikan konstanta maksimalQueue dengan nilai 5 yang mewakili kapasitas maksimum antrian. Variabel front dan back diinisialisasi dengan 0 sebagai penanda posisi elemen terdepan dan terbelakang dalam antrian. Array string queueTeller disiapkan untuk menyimpan elemen-elemen antrian.

Beberapa fungsi disediakan seperti isFull untuk mengecek apakah antrian sudah penuh, isEmpty untuk mengecek apakah antrian kosong, enqueueAntrian untuk menambahkan elemen baru ke antrian, dequeueAntrian untuk menghapus elemen dari antrian, countQueue untuk mendapatkan jumlah elemen dalam antrian, clearQueue untuk mengosongkan antrian, viewQueue untuk menampilkan isi antrian, serta displayMenu untuk menampilkan menu pilihan operasi bagi pengguna.

Pada fungsi utama main, program akan menampilkan menu pilihan dan memproses operasi yang dipilih pengguna dengan memanggil fungsi yang sesuai, seperti enqueueAntrian untuk menambah elemen, dequeueAntrian untuk menghapus elemen, dan sebagainya. 

## Kesimpulan
#### Hasil praktikum: 
Pada praktikum kali ini, Anda mempelajari dua jenis struktur data, yaitu stack dan queue. 
Stack atau tumpukan merupakan struktur data yang mengikuti aturan LIFO (Last In First Out), yang artinya data yang terakhir dimasukkan ke dalam stack akan menjadi data yang pertama kali dikeluarkan dari stack. Sedangkan queue atau antrian merupakan struktur data yang mengikuti aturan FIFO (First In First Out), yang artinya data yang pertama kali dimasukkan ke dalam antrian akan menjadi data yang pertama kali dikeluarkan dari antrian.

Jadi secara garis besar, stack mengimplementasikan konsep tumpukan dengan aturan LIFO, sementara queue mengimplementasikan konsep antrian dengan mengikuti aturan FIFO dalam pengeluaran dan pemasukan datanya.

#### Pelajaran yang didapat
Stack adalah struktur data LIFO (Last In First Out) di mana elemen terakhir yang masuk akan menjadi elemen pertama yang keluar. Operasi dasar stack meliputi push (menambah elemen), pop (mengambil elemen teratas), pengecekan kosong dan penuh.

Queue adalah struktur data FIFO (First In First Out) di mana elemen pertama yang masuk akan menjadi elemen pertama yang keluar. Operasi dasar queue mencakup enqueue (menambah elemen), dequeue (mengeluarkan elemen), peek (melihat elemen depan tanpa menghapus), pengecekan kosong dan penuh, serta penghitungan jumlah elemen.

## Referensi
[1] Johnson Sihombing, “PENERAPAN STACK DAN QUEUE PADA ARRAY DAN LINKED LIST DALAM JAVA”, 2019. 

[2] Rizaldy Gunawan, Haris Yuana, Sabitul Kirom,"IMPLEMENTASI METODE QUEUE PADA SISTEM ANTRIAN ONLINE BERBASIS WEB STUDI KASUS UPTD PUSKESMAS SANANWETAN", 2023.