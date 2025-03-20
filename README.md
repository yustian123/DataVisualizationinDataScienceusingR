# DataVisualizationinDataScienceusingR
##Membuat Kanvas Kosong
```
library(ggplot2)
ggplot()
```

##Menambahkan Judul
```
[objek plot] + labs(title="Judul")
```
##Plot disimpan sebagai Variable
```
library(ggplot2)
plot.jakarta <- ggplot()
plot.jakarta <- plot.jakarta + labs(title="Luas Wilayah vs Kepadatan Penduduk DKI Jakarta - Periode 2013")
plot.jakarta
```
##Menambahkan Label pada Sumbu X dan Y
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
