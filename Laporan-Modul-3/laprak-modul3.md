# <h1 align="center">Laporan Praktikum Modul 3 Struktur Data </h1>
<p align="center">Fadriano Bumindra Abiyyu - 109082500170</p>

## Dasar Teori
### A. Abstract Data Type (ADT) <br/>
ADT dibuat agar tipe data dan operasinya berada di dalam satu kesatuan yang rapi.
#### 1. File Header(.h)
Berisi definisi tipe dan daftar fungsi atau prosedur yang tersedia[3].
#### 2. File Body(.cpp)
Berisi isi dan fungsi dan prosedur yang sudah dideklarasikan di file header[3].
#### 3. Driver(main.cpp)
Berisi program utama yang memanggil fungsi dan prosedur tersebut untuk diuji[3].

## Guided 

### mahasiswa.h 

```C++
#ifndef MAHASISWA_H_INCLUDED
#define MAHASISWA_H_INCLUDED

struct mahasiswa{
    char nim[10];
    int nilai1, nilai2;
};

void inputMhs (mahasiswa &m) ;
float rata2 (mahasiswa m) ;
#endif // MAHASISWA_H_INCLUDED
```
Kode tersebut berisi definisi struct mahasiswa serta deklarasi prosedur inputMhs dan fungsi rata2.

### mahasiswa.cpp

```C++
#include <iostream>
#include "mahasiswa.h"

using namespace std;

void inputMhs (mahasiswa &m) {
  cout << "input nim = ";
  cin >> (m).nim;
  cout << "input nilai1 = ";
  cin >> (m).nilai1;
  cout << "input nilai2 = ";
  cin >> (m).nilai2;
}

float rata2(mahasiswa m) {
  return float(m.nilai1 + m.nilai2) / 2;
}
```
Kode tersebut berisi implementasi atau logika pemrograman dari prosedur inputMhs dan fungsi rata2.

### main.cpp 

```C++
#include <iostream>
#include "mahasiswa.h"

using namespace std;

int main() 
{
  mahasiswa mhs;
  inputMhs(mhs);
  cout << "rata-rata = " << rata2(mhs);
  return 0;
}
```
Kode tersebut berisi program utama yang memanggil prosedur inputMhs dan fungsi rata2.

## Unguided 

### 1. Buatlah progam yang dapat menyimpan data mahasiswa (max. 10) ke dalam sebuah array dengan field nama, nim, uts, uas, tugas, dan nilai akhir. Nilai akhir diperoleh dari FUNGSI dengan rumus 0.3 * uts+0.4 * uas+0.3 * tugas.

```C++
#include <iostream>
#include <string>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    float uts;
    float uas;
    float tugas;
    float nilaiAkhir;
};

float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return 0.3 * uts + 0.4 * uas + 0.3 * tugas;
}

int main() {
    Mahasiswa mhs[10];
    int n, i;

    cout << "Jumlah mahasiswa (maks 10): ";
    cin >> n;

    if (n < 1 || n > 10) {
        cout << "Jumlah mahasiswa harus antara 1 dan 10" << endl;
        return 1;
    }

    cin.ignore();

    for (i = 0; i < n; i++) {
        cout << "\nData mahasiswa ke-" << i + 1 << endl;
        cout << "Nama   : ";
        getline(cin, mhs[i].nama);
        cout << "NIM    : ";
        cin >> mhs[i].nim;
        cout << "UTS    : ";
        cin >> mhs[i].uts;
        cout << "UAS    : ";
        cin >> mhs[i].uas;
        cout << "Tugas  : ";
        cin >> mhs[i].tugas;
        cin.ignore();
        mhs[i].nilaiAkhir = hitungNilaiAkhir(mhs[i].uts, mhs[i].uas, mhs[i].tugas);
        cout << "Nilai Akhir: " << mhs[i].nilaiAkhir << endl;
    }
    return 0;
}
```
### Output Unguided 1 :
Jumlah mahasiswa (maks 10): 2

Data mahasiswa ke-1
Nama   : Asep
NIM    : 109082500000
UTS    : 90
UAS    : 80
Tugas  : 70
Nilai Akhir: 80

Data mahasiswa ke-2
Nama   : Sugeng
NIM    : 109082599999
UTS    : 95
UAS    : 85
Tugas  : 87
Nilai Akhir: 88.6

##### Output
![Screenshot Output Unguided 1_1](https://github.com/fadrianooo/Laporan-Praktikum-Modul3/blob/main/Laporan-Modul-3/Output-Unguided/Output-Unguided-1_1.png)

Proram ini menyimpan data mahasiswa dalam array struct dan menghitung nilai akhirnya dengan fungsi hitungNilaiAkhir.

### 2. Buatlah ADT pelajaran yang dipisah menjadi berkas pelajaran.h, pelajaran.cpp, dan main.cpp sesuai spesifikasi soal.

#### A. pelajaran.h
```C++
#ifndef PELAJARAN_H_INCLUDED
#define PELAJARAN_H_INCLUDED

#include <string>
using namespace std;

struct pelajaran {
    string namaMapel;
    string kodeMapel;
};

pelajaran create_pelajaran(string namapel, string kodepel);
void tampil_pelajaran(pelajaran pel);

#endif
```
#### B. pelajaran.cpp
```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

pelajaran create_pelajaran(string namapel, string kodepel) {
    pelajaran p;
    p.namaMapel = namapel;
    p.kodeMapel = kodepel;
    return p;
}

void tampil_pelajaran(pelajaran pel) {
    cout << "nama pelajaran : " << pel.namaMapel << endl;
    cout << "nilai : " << pel.kodeMapel << endl;
}
```
#### C. main.cpp
```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

int main() {
    string namapel = "Struktur Data";
    string kodepel = "STD";
    pelajaran pel = create_pelajaran(namapel, kodepel);
    tampil_pelajaran(pel);

    return 0;
}
```
### Output Unguided 2 :
nama pelajaran : Struktur Data
nilai : STD
##### Output
![Screenshot Output Unguided 2_1](https://github.com/fadrianooo/Laporan-Praktikum-Modul3/blob/main/Laporan-Modul-3/Output-Unguided/Output-Unguided-2_1.png)

Program ini menggunakan ADT pelajaran dengan fungsi create_pelajaran untuk membentuk data dan prosedur tampil_pelajaran untuk menampilkannya.

### 3. Buatlah program dengan ketentuan : - 2 buah array 2D integer berukuran 3x3 dan 2 buah pointer integer. - fungsi/prosedur yang menampilkan isi sebuah array integer 2D. - fungsi/prosedur yang akan menukarkan isi dari 2 array integer 2D pada posisi tertentu. - fungsi/prosedur yang akan menukarkan isi dari variabel yang ditunjuk oleh 2 buah pointer.

```C++
#include <iostream>
using namespace std;

void tampilArray(int arr[3][3]) {
    int i, j;
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 3; j++) {
            cout << arr[i][j] << "\t";
        }
        cout << endl;
    }
}
void tukarPosisi(int a[3][3], int b[3][3], int baris, int kolom) {
    int temp;
    temp = a[baris][kolom];
    a[baris][kolom] = b[baris][kolom];
    b[baris][kolom] = temp;
}
void tukarPointer(int *p, int *q) {
    int temp;
    temp = *p;
    *p = *q;
    *q = temp;
}
int main() {
    int A[3][3] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    int B[3][3] = {{10, 20, 30}, {40, 50, 60}, {70, 80, 90}};
    int *p1 = &A[0][0];
    int *p2 = &B[2][2];

    cout << "SEBELUM" << endl;
    cout << "Array A:" << endl;
    tampilArray(A);
    cout << "Array B:" << endl;
    tampilArray(B);
    cout << "Pointer: *p1 = " << *p1 << ", *p2 = " << *p2 << endl;

    tukarPosisi(A, B, 1, 1);
    tukarPointer(p1, p2);

    cout << "\nSESUDAH" << endl;
    cout << "Array A:" << endl;
    tampilArray(A);
    cout << "Array B:" << endl;
    tampilArray(B);
    cout << "Pointer: *p1 = " << *p1 << ", *p2 = " << *p2 << endl;

    return 0;
}
```
### Output Unguided 3 :
SEBELUM
Array A:
1       2       3
4       5       6
7       8       9
Array B:
10      20      30
40      50      60
70      80      90
Pointer: *p1 = 1, *p2 = 90

SESUDAH
Array A:
90      2       3
4       50      6
7       8       9
Array B:
10      20      30
40      5       60
70      80      1
Pointer: *p1 = 90, *p2 = 1
##### Output 1
![Screenshot Output Unguided 3_1](https://github.com/fadrianooo/Laporan-Praktikum-Modul3/blob/main/Laporan-Modul-3/Output-Unguided/Output-Unguided-3_1.png)

Kode tersebut berisi dua array 2D berukuran 3x3 dan dua pointer integer. Prosedur tampilArray menampilkan isi array, tukarPosisi menukan isi dua array pada posisi tertentu, dan tukarPointer menukar nilai variabel yang ditunjuk oleh dua pointer.

## Kesimpulan
ADT memisahkan definisi tipe, isi fungsi, dan program utama ke dalam file yang berbeda sehingga program lebih rapi. Pada praktikum ini memberikan saya pemahaman konsep ADT dan implementasinya pada c++, seperti dengan memisahkan program menjadi file header, .cpp, dan main.cpp.

## Referensi
[1] Maylova, R. A., Noviana, N., Abdussalam, A., Pramudya, E. R., & Muslih, M. (2025). "Sistem Manajemen Data Mahasiswa Berbasis Pemrograman C++ untuk Efisiensi Administrasi Akademik". Jurnal Aplikasi Teknologi dan Komputasi, 1(3), 24-33. Diakses pada 9 Oktober 2026 melalui https://journals.arces.org/jatekom/article/view/83. <br>
[2] Budiman, Alamsyah, N., & Al Rasyid, A. (2023). "Buku Ajar Pemrograman C++". Bandung: Unibi Press. ISBN 978-623-99962-3-9. Diakses pada 9 Oktober 2026 melalui https://repository.unibi.ac.id/531/1/PEMROGRAMAN%20C%2B%2B.pdf. <br>
[3] Modul Praktikum Struktur Data. (n.d.). "Modul 3: Abstract Data Type (ADT)". Bahan ajar praktikum.