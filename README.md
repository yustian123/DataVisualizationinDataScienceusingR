# DataVisualizationinDataScienceusingR
##Membuat Kanvas Kosong
```
library(ggplot2)
ggplot()
```

## Menambahkan Judul
```
[objek plot] + labs(title="Judul")
```
## Plot disimpan sebagai Variable
```
library(ggplot2)
plot.jakarta <- ggplot()
plot.jakarta <- plot.jakarta + labs(title="Luas Wilayah vs Kepadatan Penduduk DKI Jakarta - Periode 2013")
plot.jakarta
```
## Menambahkan Label pada Sumbu X dan Y
```
[objek plot] + labs(x="Label X", y = "Label Y")
```
Contoh
```
library(ggplot2)
plot.jakarta <- ggplot()
plot.jakarta <- plot.jakarta + labs(title="Luas Wilayah vs Kepadatan Penduduk DKI Jakarta - Periode 2013", subtitle="Tahun 2013")
plot.jakarta <- plot.jakarta + labs(x="Luas Wilayah (km2)", y = "Kepadatan Jiwa per km2")
plot.jakarta
```
## Fungsi summary untuk objek ggplot
Melihat detilnya dalam bentuk tekstual dengan menggunakan fungsi summary.
```
library(ggplot2)
plot.jakarta <- ggplot()
plot.jakarta <- plot.jakarta + labs(title="Luas Wilayah vs Kepadatan Penduduk DKI Jakarta")
plot.jakarta <- plot.jakarta + labs(x = "Luas Wilayah (km2)", y="Kepadatan Jiwa per km2")
summary(plot.jakarta)
```
## Membaca Dataset Kependudukan dengan read.csv
```
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
```
## Menampilkan beberapa kolom tertentu
```
library(ggplot2)
#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
# Masukkan data ke dalam plot dan simpan sebagai variable plot.dki, dan tampilkan summary dari plot tersebut
plot.dki <- ggplot(data = penduduk.dki)
summary(plot.dki)
```
grafik bisa dihasilkan dengan menambahkan layer secara berlapis di atas plot.

Setiap layer terdiri dari objek-objek berikut:

Geom: Bentuk geometri seperti garis (line), batang (bar), titik (point), dan lain-lain.
Stat: Atau suatu fungsi untuk melakukan transformasi statistik terhadap data input.
Contoh paling sederhana adalah transformasi data untuk kepadatan jiwa dari angka menjadi range atau inverval per lima ribuan. Jadi data input dengan angka 8041 diubah menjadi interval angka 8001-8500. Transformasi ini disebut dengan bin. Jika kita tidak ingin mengubah apa-apa, stat yang kita gunakan adalah identity.
Position: Posisi dari beberapa data yang memiliki nilai yang sama. Jika diplot sebagai scatter plot misalnya, tentunya data-data tersebut akan menumpuk di satu titik. Apakah perlu ditambahkan nilai acak tertentu sehingga pas digambarkan, terlihat datanya lebih tersebar? Jika iya, maka ini namanya jitter. Jika kita tidak ingin merubah posisi, maka kita gunakan identity.

## Scatter Plot Kepadatan Penduduk Jakarta dengan function layer
```
library(ggplot2)
#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.dki <- ggplot(data=penduduk.dki, aes(x = LUAS.WILAYAH..KM2.,  y=KEPADATAN..JIWA.KM2.,  color=NAMA.KABUPATEN.KOTA))

#Menambahkan layer untuk menghasilkan grafik scatter plot
plot.dki + layer(geom = "point", stat = "identity", position = "identity")
```
## Scatter Plot Kepadatan Penduduk Jakarta dengan geom_point
```
library(ggplot2)
#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.dki <- ggplot(data=penduduk.dki, aes(x = LUAS.WILAYAH..KM2.,  y=KEPADATAN..JIWA.KM2.,  color=NAMA.KABUPATEN.KOTA))

#Menambahkan layer scatter plot dengan geom_point
plot.dki + geom_point()
```
## Menambahkan Judul dan Label

