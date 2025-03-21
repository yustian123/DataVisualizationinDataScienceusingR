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
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.dki <- ggplot(data=penduduk.dki, aes(x = LUAS.WILAYAH..KM2.,  y=KEPADATAN..JIWA.KM2.,  color=NAMA.KABUPATEN.KOTA))

#Menambahkan Layer dan labels
plot.dki + geom_point() + 
  theme(plot.title = element_text(hjust=0.5)) + labs(title = "Luas Wilayah vs Kepadatan Penduduk DKI Jakarta", x = "Luas wilayah (km2)", y = "Kepadatan Jiwa per km2", color = "Nama Kabupaten/Kota")
```
Pada code terdapat perintah baru, yaitu theme(plot.title = element_text(hjust=0.5)). Ini adalah code untuk menempatkan judul di tengah plot.
## Histogram
Histogram adalah tipe visualisasi yang sangat cocok untuk menggambarkan data distribusi dari jumlah populasi data. Dan dataset kependudukan adalah contoh yang baik dimana kita bisa menggambarkan distribusi kepadatan penduduk dengan jumlah kelurahan.

Untuk membuat histogram, kita gunakan geom bertipe histogram dan stat bin, yang bisa diwakili oleh function geom_histogram.
### Layer geom_histogram dan Lebar Interval
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.dki <- ggplot(data=penduduk.dki, aes(x = KEPADATAN..JIWA.KM2.))
plot.dki + geom_histogram(binwidth=10000)
```
binwidth = Lebar interval data, dalam hal ini 5000
### Penggunaaan aesthetic fill
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

plot.dki <- ggplot(data=penduduk.dki, aes(x = KEPADATAN..JIWA.KM2., fill = NAMA.KABUPATEN.KOTA))

plot.dki + geom_histogram(binwidth = 10000)
```
## Line chart
Line chart atau grafik garis adalah tipe visualisasi yang sangat baik untuk menggambarkan apa impact (pengaruh) dari perubahan suatu variabel dari satu titik ke titik lain atau trend– dan variabel yang paling umum digunakan adalah waktu.

Sebagai contoh, di bidang ekonomi untuk menggambarkan inflasi dari bulan ke bulan. Namun tentunya tidak harus selalu waktu. Perubahan lain, misalkan pengaruh kecepatan lari dengan peningkatan detak jantung.

Untuk membuat line chart standar, kita gunakan geom bertipe "line" dan stat "identity", yang bisa diwakili oleh function geom_line.
### Membaca data inflasi
```
#Membaca data csv dan dimasukkan ke variable inflasi.indo.sing
inflasi.indo.sing <- read.csv("https://storage.googleapis.com/dqlab-dataset/inflasi.csv", sep=",")
inflasi.indo.sing
```
### Plotting Line Chart yang Kosong
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable inflasi.indo.sing
inflasi.indo.sing <- read.csv("https://storage.googleapis.com/dqlab-dataset/inflasi.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.inflasi <- ggplot(data=inflasi.indo.sing, aes(x = Bulan,  y=Inflasi,  color=Negara))

#Menambahkan layer
plot.inflasi + geom_line()
```
### Menggunakan Pengelompokan Data (grouping)
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable inflasi.indo.sing
inflasi.indo.sing <- read.csv("https://storage.googleapis.com/dqlab-dataset/inflasi.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.inflasi <- ggplot(data=inflasi.indo.sing, aes(x = Bulan,  y=Inflasi,  color=Negara, group=Negara))

#Menambahkan Layer
plot.inflasi + geom_line()
```
### Memperbaiki Urutan Bulan dengan Factoring
```
library(ggplot2)
#Membaca data csv dan dimasukkan ke variable inflasi.indo.sing
inflasi.indo.sing <- read.csv("https://storage.googleapis.com/dqlab-dataset/inflasi.csv", sep=",")
inflasi.indo.sing$Bulan <- factor(inflasi.indo.sing$Bulan, levels = c("Jan-2017", "Feb-2017", "Mar-2017", "Apr-2017", "May-2017", "Jun-2017", "Jul-2017", "Aug-2017", "Sep-2017", "Oct-2017"))

str(inflasi.indo.sing)
```
### Plotting Ulang dengan hasil Factoring Dengan proses perbaikan
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable inflasi.indo.sing
inflasi.indo.sing <- read.csv("https://storage.googleapis.com/dqlab-dataset/inflasi.csv", sep=",")

inflasi.indo.sing$Bulan = factor(inflasi.indo.sing$Bulan, 
                                 levels = c("Jan-2017", "Feb-2017", "Mar-2017", "Apr-2017", "May-2017", "Jun-2017", "Jul-2017", "Aug-2017", "Sep-2017", "Oct-2017"))

#Menambahkan data dan aesthetic mapping
plot.inflasi <- ggplot(data=inflasi.indo.sing, aes(x = Bulan,  y=Inflasi,  color=Negara, group=Negara))


#Menambahkan Layer dan labels
plot.inflasi + geom_line() + geom_text(aes(label=Inflasi),hjust=-0.2, vjust=-0.5)

```
## Bar chart dan Pie chart
Bar chart atau grafik batang adalah salah satu tipe visualisasi yang sudah umum digunakan yang sangat baik untuk melakukan perbandingan data multi kategori. Sedangkan pie chart sangat berguna untuk melihat rasio.
### Menghasilkan Bar Chart Pertama
```
library(ggplot2)
#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")
plot.dki <- ggplot(data=penduduk.dki, aes(x = NAMA.KABUPATEN.KOTA))
plot.dki + geom_bar()
```
### Aesthetic Y dan Stat Identity
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")

#Menghasilkan bar chart

#Membuat plot
plot.dki <- ggplot(data=penduduk.dki, aes(x = NAMA.KABUPATEN.KOTA, y = JUMLAH))

#Menambahkan layer pada plot
plot.dki + geom_bar(stat = "identity")
```
### Aesthetic Fill dan Position Dodge
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")

#Bagian plot
plot.dki <- ggplot(data=penduduk.dki, aes(x = NAMA.KABUPATEN.KOTA, y=JUMLAH, fill = JENIS.KELAMIN))

#Bagian penambahan layer
plot.dki + geom_bar(stat="identity", position = "dodge")
```
### Fungsi Aggregate
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")
#Melakukan agregasi
aggregate(x=list(RATARATA=penduduk.dki$JUMLAH), FUN=mean, by = list(NAMA.KABUPATEN.KOTA=penduduk.dki$NAMA.KABUPATEN.KOTA, JENIS.KELAMIN=penduduk.dki$JENIS.KELAMIN))
```
Sum
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")
#Melakukan agregasi
aggregate(x=list(JUMLAH=penduduk.dki$JUMLAH), FUN=sum, by = list(NAMA.KABUPATEN.KOTA=penduduk.dki$NAMA.KABUPATEN.KOTA, JENIS.KELAMIN=penduduk.dki$JENIS.KELAMIN))
```
### "Merapikan" Tampilan Bar Chart
```
library(ggplot2)
#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")
#Melakukan agregasi
p <- aggregate(x=list(JUMLAH=penduduk.dki$JUMLAH), FUN=sum, by = list(NAMA.KABUPATEN.KOTA=penduduk.dki$NAMA.KABUPATEN.KOTA, JENIS.KELAMIN=penduduk.dki$JENIS.KELAMIN))

#Plot grafik
plot.dki <- ggplot(data=p, aes(x = NAMA.KABUPATEN.KOTA, y=JUMLAH, fill=JENIS.KELAMIN, label = JUMLAH))
plot.dki <- plot.dki + geom_bar(stat="identity", position="dodge")  
plot.dki <- plot.dki + labs(title="Jumlah Penduduk DKI Jakarta Umur > 35 - Tahun 2013", x="Kabupaten / Kota", y="Jumlah Penduduk")
plot.dki <- plot.dki + theme(axis.text.x = element_text(angle=45,vjust = 0.5), plot.title = element_text(hjust=0.5))
plot.dki <- plot.dki + geom_text(position = position_dodge(1.2))
plot.dki
```
### Pie Chart dengan Koordinat Polar
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/datakependudukandki-dqlab.csv", sep=",")
#Melakukan agregasi
p <- aggregate(x=list(JUMLAH=penduduk.dki$JUMLAH), FUN=sum, by = list(NAMA.KABUPATEN.KOTA=penduduk.dki$NAMA.KABUPATEN.KOTA))
#Plot grafik pie chart
plot.dki <- ggplot(data=p, aes(x="", y=JUMLAH, fill = NAMA.KABUPATEN.KOTA))

plot.dki <- plot.dki + geom_bar(width = 1, stat = "identity")
plot.dki <- plot.dki + coord_polar("y", start=0)
plot.dki
```
## Membagi Grafik dengan Faceting
Faceting pada ggplot2 adalah:

Proses pembagian dataset menjadi potongan beberapa subset data
dan menghasilkan visualisasi dari potongan-potongan tersebut
dengan tujuan agar data lebih mudah dimengerti
### Faceting pada Scatter Plot
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.dki <- ggplot(data=penduduk.dki, aes(x = LUAS.WILAYAH..KM2.,  y=KEPADATAN..JIWA.KM2.,  color=NAMA.KABUPATEN.KOTA))

#Menambahkan layer
plot.dki <- plot.dki + layer(geom = "point", stat="identity", position = "identity")
plot.dki <- plot.dki + labs(x="Luas Wilayah (km2)", y="Kepadatan Jiwa (km2)", color="Kabupaten/Kota")
plot.dki + facet_wrap( ~ NAMA.KABUPATEN.KOTA, ncol=2)
```
### Faceting pada Histogram
```
library(ggplot2)

#Membaca data csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")

#Menambahkan data dan aesthetic mapping
plot.dki <- ggplot(data=penduduk.dki, aes(x=KEPADATAN..JIWA.KM2.,  fill=NAMA.KABUPATEN.KOTA))

#Menambahkan layer
plot.dki <- plot.dki + geom_histogram(binwidth=10000)
plot.dki <- plot.dki + labs(x="Kepadatan Jiwa (km2)", y="Jumlah Kelurahan", color="Kabupaten/Kota")
plot.dki + facet_wrap( ~ NAMA.KABUPATEN.KOTA, ncol=2)
```
