```
update!(repo::GitRepo, files::AbstractString...)
update!(idx::GitIndex, files::AbstractString...)
```

`files` ile belirtilen yollarla tüm dosyaları `idx` (veya `repo`'nun indeksinde) güncelleyin. Her dosyanın indeksindeki durumunu disk üzerindeki mevcut durumla eşleştirin, diskten kaldırılmışsa onu kaldırın veya nesne veritabanındaki girişini güncelleyin.
