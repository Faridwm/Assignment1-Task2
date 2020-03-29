### Farid Wujdi Mubarok
### 1313617006
### Sistem Pakar Semester 112
### Assigment 1
### Task 2: 2D Rotation

# 3D Rotasi Axis
Rotasi ini direpresentasikan oleh rotasi pada sumbu n^ dan berputar sebesar sudut *theta* dengan satuan radian atau degree (pada source code saya menggunakan degree). n^ merupakan vector dengan nilai acak yang terdiri dari n^x, n^y dan n^z dan memiliki magnitude (panjang vector) = 1 agar rotasi sempurna.

### Cara kerja 3D rotasi Axis
3D rotasi axis bekerja dengan memutar objek 3d berdasarkan sumbu rotasi menurut n^, dan diputar sebesar *theta*. 

### Algoritma ke kode
Rotasi axis memerlukan matrix input, n^ yang merupakan vector dengan nilai acak, sudut *theta* dengan satuan degree yang kemudian di konversi mendjadi radian. 
Pertama saya deklarasiakn matrix identitas berukuran 3x3. setelah itu memecah n^ menjadi n^x, n^y, n^z dan memasukkannya ke dalam notasi
```code
[n^]x = [
          [0, -n^z, n^y],
          [n^z, 0, -n^x],
          [-n^y, n^x, 0]
        ]
```
setelah mendapatkan matrix [n^]x, maka kita dapat langsung masuk kedalam rumus Rodriguez sebagai berikut
```code
R(n^, theta) = I + sin(theta) * [n^]x + (1 - cos(theta)) * ([n^]x * [n^]x)
```
untuk mendapatkan matriks pengali rotasi axis.
terakhir kita kalikan matrix R dengan matriks titik objek 3D.

### Kesimpulan dari eksperimen dengan rotasi axis
dengan menggunakan n^ yang memiliki magnitude < 1 maka objek akan berotasi sedikit. Jika magnitude dari n^ = 1 maka rotasi akan sempurna, dan jika magnitude n^ > 1 maka objek akan semakin besar dan pipih


# 3D Rotasi Unit Quartenion
Unit quartenion merupakan penurunan rumus rodriguez dari rotasi axis, quartenion dapat diturunkan dari representasi sumbu / sudut melalui rumus
```code
q = (v, w) = (sin (theta/2) * n^, cos(theta/2))
```
dengan memecah v didapat v = (x, y, z)
maka didapat

```code
[v^]x = [
          [0, -z, y],
          [z, 0, -x],
          [-y, x, 0]
        ]
```

sehingga turunan rumus rodriguez didapat
```code
R(n^, theta) = I + sin(theta) * [n^]x + (1 - cos(theta)) * ([n^]x * [n^]x)

R(n^, theta) = I + w * [v^]x + (2 * ([v^]x * [v^]x))
```

### Algoritma ke kode
Rotasi unit quartenion memerlukan bahan yang sama dengan rotasi axis yaitu matrix input, n^ yang merupakan vector dengan nilai acak, sudut *theta* dengan satuan degree yang kemudian di konversi mendjadi radian.
Pertama deklarasikan matrix identitas berukuran 3x3, lalu cari nilai v dan w dengan rumus 
```code
q = (v, w) = (sin (theta/2) * n^, cos(theta/2))
```

setelah itu pecah v menjadi (x, y, z) untuk mendapatkan matriks [v^]x, dimana
```code
[v^]x = [
          [0, -z, y],
          [z, 0, -x],
          [-y, x, 0]
        ]
```

setelah itu kita dapat memasukkan ke dalam rumus
```code
R(n^, theta) = I + w * [v^]x + (2 * ([v^]x * [v^]x))
```
untuk mendapatkan matriks pengali rotasi unit quartenion
terakhir kita kalikan matrix R dengan matriks titik objek 3D.


### Kesimpulan dari eksperimen dengan rotasi unit quartenion
