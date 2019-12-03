## Pricing Costing Marketing

**Overview :**
> Modul *pricing costing marketing* adalah langkah selanjutnya setelah dilakukan input biaya costing di *desktop*. *Pricing* digunakan untuk menentukan estimasi harga jual *kurs* per satuan terkecil atau satuan terbesar maupun *margin profit* sehingga didapatkan estimasi laba dalam *kurs* maupun rupiah.  Input biaya *costing* digunakan untuk menentukan biaya-biaya yang mempengaruhi hpp dari sebuah *product*. Input biaya costing digunakan untuk menginputkan *costing* per *product*. Jadi, dalam satu kali permintaan *costing* memungkinkan ada beberapa *product* untuk satu *customer*. Dan masing - masing product memiliki *costing* sendiri.

**Rules :**

1. *Kurs* yang digunakan mengikuti *kurs* yang telah dipilih pada saat permintaan *costing marketing*. Tetapi dapat diubah sesuai dengan kebutuhan.
2. Dalam pricing costing pembulatan menggunakan pembulatan 4 angka dibelakang koma ',' 
3. *Margin profit* digunakan untuk menghitung laba berdasarkan persentase (%) dari estimasi hpp kurs per satuan terbesar dan satuan terkecil. Jadi,  ``est harga jual satuan terbesar = hpp kurs satuan terbesar + hpp kurs satuan terbesar * (marginprofit/100)`` ``est harga jual satuan terkecil = hpp kurs satuan terkecil + hpp kurs satuan terkecil * (marginprofit/100)`` ``est omset (kurs) = jumlah pesanan * est harga jual satuan terbesar`` ``est omset (rupiah) = est omset (kurs) * nilai kurs `` ``est laba (rupiah) = est omset (rupiah) - hpp total rupiah  `` 
4. *Est harga jual satuan terbesar* digunakan untuk menghitung laba berdasarkan estimasi harga jual per satuan terbesar. Jadi, ``Margin Profit = ((Est harga jual satuan terbesar - kurs satuan terbesar ) / kurs satuan terbesar ) * 100`` ``est harga jual satuan terkecil = hpp kurs satuan terkecil + hpp kurs satuan terkecil * (marginprofit/100)`` ``est omset (kurs) = jumlah pesanan * est harga jual satuan terbesar`` ``est omset (rupiah) = est omset (kurs) * nilai kurs `` ``est laba (rupiah) = est omset (rupiah) - hpp total rupiah``

 