# PROJEK UAS PENGOLAHAN CITRA A

Perkenalkan saya Muhammad Amar Mahdin 202131043. Pada project ini saya mendapatkan judul DETEKSI PLAT NOMOR. 

Sebelum ke program, terlebih dahulu saya akan menjelaskan apa itu Deteksi Plat Nomor dan kegunannya. 

## Deteksi Plat Nomor
Deteksi plat nomor adalah proses komputerisasi untuk mengenali dan memperoleh informasi dari plat nomor kendaraan yang terdapat dalam gambar atau video. Tujuan dari deteksi plat nomor adalah untuk mengotomatisasi dan mempermudah proses identifikasi kendaraan, seperti yang sering dilakukan dalam sistem keamanan lalu lintas, sistem parkir otomatis, atau penegakan hukum.

Proses deteksi plat nomor melibatkan beberapa langkah. Pertama, algoritma pengolahan citra digunakan untuk mengenali dan memisahkan wilayah plat nomor dari gambar atau video yang lebih besar. Kemudian, teknik pengolahan citra lebih lanjut diterapkan untuk meningkatkan kejelasan dan kekontrasan plat nomor yang terdeteksi.

Setelah itu, deteksi karakter atau Optical Character Recognition (OCR) diterapkan pada wilayah plat nomor yang telah diisolasi. OCR menggunakan algoritma untuk mengenali dan mengubah karakter plat nomor menjadi teks yang dapat dibaca oleh mesin. Informasi ini kemudian dapat digunakan untuk mengidentifikasi kendaraan, memeriksa keabsahan plat nomor, dan melakukan tindakan lainnya seperti pencarian dalam basis data atau perbandingan dengan daftar kendaraan yang dicurigai.

Deteksi plat nomor telah menjadi aplikasi yang penting dalam berbagai bidang, termasuk sistem keamanan, pengawasan lalu lintas, dan pengenalan kendaraan otomatis.

## Penjelasan Program

### Import Library

    import cv2 as cv
    import matplotlib.pyplot as plt
    import imutils

import cv2 as cv Mengimport modul OpenCV dengan alias cv. import matplotlib.pyplot as plt Mengimport modul pyplot dari library Matplotlib dengan alias plt. import imutils mengimport modul imutils. Modul ini menyediakan beberapa fungsi utilitas yang berguna untuk mempermudah pemrosesan gambar, seperti resizing, rotasi, dan pergeseran gambar. Modul ini biasanya digunakan bersamaan dengan OpenCV untuk mempermudah manipulasi gambar.

    plat = cv.imread("plat.jpg")

cv.imread("plat.jpg") mengambil gambar dengan nama file "plat.jpg" dan membacanya ke dalam bentuk matriks/array menggunakan fungsi imread dari OpenCV.

    plat1 = cv.cvtColor(plat,cv.COLOR_BGR2GRAY)
    img_crop = plat1[430:505,260:470]

plat1 = cv.cvtColor(plat, cv.COLOR_BGR2GRAY): Mengkonversi gambar plat dari mode warna BGR (Blue-Green-Red) ke mode grayscale (skala keabuan) menggunakan fungsi cvtColor dari OpenCV. 
img_crop = plat1[430:505, 260:470]: Membuat sub-gambar (crop) dari gambar plat1 dengan mengambil sebagian area gambar dari baris 430 hingga 504 dan kolom 260 hingga 469. 

    (these, imgb) = cv.threshold(img_crop, 0,255, cv.THRESH_BINARY + cv.THRESH_OTSU)

    edge = cv.Canny(img_crop, 100, 150)

(thresh, imgb) = cv.threshold(img_crop, 0, 255, cv.THRESH_BINARY + cv.THRESH_OTSU): Pada operasi ini, digunakan fungsi cv.threshold dari OpenCV untuk melakukan thresholding pada gambar img_crop.
edge = cv.Canny(img_crop, 100, 150): Pada operasi ini, digunakan fungsi cv.Canny dari OpenCV untuk mendeteksi tepi pada gambar img_crop. 

    fig, axes = plt.subplots(1, 4, figsize = (10, 11))
    ax = axes.ravel()

    # Menampilkan Gambar asli dan Plat Terdeteksi
    ax[0].imshow(plat)
    ax[0].set_title('Gambar Asli')
    ax[1].imshow(img_crop, cmap = 'gray')
    ax[1].set_title('Plat Terdeteksi')

    # Menampilkan Hasil binary dan Setelah edges
    ax[2].imshow(cv.cvtColor(imgb, cv.COLOR_BGR2RGB))
    ax[2].set_title('Hasil Binary')
    ax[3].imshow(edge, cmap = 'gray')
    ax[3].set_title('Setelah Edges')

fig, axes = plt.subplots(1, 4, figsize=(10, 11)): Membuat suatu objek Figure dan beberapa objek Axes menggunakan subplots() dari plt. Di sini, subplots(1, 4) menghasilkan satu baris dan empat kolom subplot. figsize=(10, 11) mengatur ukuran figur dengan lebar 10 inci dan tinggi 11 inci. Hasilnya disimpan dalam variabel fig dan axes.
ax = axes.ravel() membentuk array 1D dari objek axes dengan menggunakan fungsi ravel(). Hal ini berguna untuk mengakses setiap objek Axes secara individu dalam loop berikutnya.

ax[0].imshow(plat) menampilkan gambar asli dalam objek ax[0] menggunakan imshow() dari ax. Gambar tersebut ditampilkan menggunakan metode default (warna asli).

ax[0].set_title('Gambar Asli') memberikan judul "Gambar Asli" pada objek ax[0] menggunakan set_title().

ax[1].imshow(img_crop, cmap='gray') menampilkan gambar img_crop (plat terdeteksi) dalam objek ax[1] menggunakan imshow(). cmap='gray' mengatur plot menggunakan skala keabuan.

ax[1].set_title('Plat Terdeteksi') memberikan judul "Plat Terdeteksi" pada objek ax[1] menggunakan set_title().

ax[2].imshow(cv.cvtColor(imgb, cv.COLOR_BGR2RGB)) menampilkan hasil binary pada objek ax[2] menggunakan imshow(). cv.cvtColor(imgb, cv.COLOR_BGR2RGB) mengonversi gambar biner ke format warna RGB untuk ditampilkan dengan benar oleh imshow().

ax[2].set_title('Hasil Binary') memberikan judul "Hasil Binary" pada objek ax[2] menggunakan set_title().

ax[3].imshow(edge, cmap='gray') menampilkan hasil edges pada objek ax[3] menggunakan imshow(). cmap='gray' mengatur plot menggunakan skala keabuan.

ax[3].set_title('Setelah Edges') memberikan judul "Setelah Edges" pada objek ax[3] menggunakan set_title().

## Sumber 
https://www.kangghani.com/2021/02/deteksi-dan-membaca-plat-kendaraan-otomatis-python.html?m=1
