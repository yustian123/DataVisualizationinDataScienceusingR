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
