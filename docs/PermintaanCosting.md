## Permintaan Costing Marketing

**Overview :**
> Modul permintaan *costing marketing* adalah tahap awal untuk menentukan estimasi harga jual yang nantinya akan dihitung berdasarkan *margin profit*, estimasi harga jual (kurs) per satuan satuan terbesar atau satuan terkecil dari total *costing* per *product*. Dalam satu kali permintaan *costing* untuk setiap *customer*, dapat digunakan untuk beberapa *finish product* sekaligus. Data *finish product* didapatkan dari *master finish product* di *desktop*.

**Rules :**

1. Kurs yg digunakan untuk permintaan costing markeeting merupakan kurs terbaru yang diambil dari nilai tengah antara kurs jual dan kurs beli yang diupdate otomatis untuk setiap 30 menit berdasarkan kurs BI (https://www.bi.go.id/id/moneter/informasi-kurs/transaksi-bi/Default.aspx)  
2. Jumlah pesanan untuk setiap *product* berdasarkan satuan terpilih 
3. Satuan default setelah memilih *product* adalah 'MC' dan jika dalam product yang terpilih tidak ada satuan 'MC' maka yang digunakan adalah satuan terbesar dari *product* tersebut
4. Untuk menentukan harga size patokan dan harga size costing didapatkan dengan parameter 'kdjenisrm' dan 'size' dari product terpilih. Dan sebagai patokan untuk menentukan harganya ada master harga rm yg berisikan range bawah dan atas untuk menentukan harga
5. Qty Exp (kg) didapatkan dari ((jumlah pesanan x berat(pcs/lbs) x berat (GR/pcs))/1000) dibagi 1000 karena dalam satuan kg
6. Qty HO (kg) didapatkan dari (jumlah pesanan * berat ho per mc)
7. Subtotal didapatkan dari (harga size costing * Qty HO (kg))
 