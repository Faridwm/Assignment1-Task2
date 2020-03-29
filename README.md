### Farid Wujdi Mubarok
### 1313617006
### Sistem Pakar Semester 112
### Assigment 1
### Task 2: 2D Rotation

# 3D Rotasi Axis
Rotasi ini direpresentasikan oleh rotasi pada sumbu n^ dan berputar sebesar sudut *theta* dengan satuan radian atau degree (pada source code saya menggunakan degree). n^ merupakan vector dengan nilai acak yang terdiri dari n^x, n^y dan n^z dan memiliki magnitude (panjang vector) = 1 agar rotasi sempurna.

### Cara kerja 3D rotasi Axis
3D rotasi axis bekerja dengan memutar objek 3d berdasarkan sumbu rotasi menurut n^

### Algoritma ke kode
Rotasi axis memerlukan input n^ yang merupakan vector dengan nilai acak, sudut *theta* dengan satuan degree yang kemudian di konversi mendia radian. 
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

### Kesimpulan dari eksperiman dengan rotasi axis
dengan menggunakan n^ yang memiliki magnitude < 1 maka objek akan berotasi sedikit. Jika magnitude dari n^ = 1 maka rotasi akan sempurna, dan jika magnitude n^ > 1 maka objek akan semakin besar dan pipih 
