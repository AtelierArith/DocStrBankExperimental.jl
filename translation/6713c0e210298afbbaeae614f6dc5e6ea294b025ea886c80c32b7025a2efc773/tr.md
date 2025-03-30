```
remove!(repo::GitRepo, files::AbstractString...)
remove!(idx::GitIndex, files::AbstractString...)
```

`idx` (veya `repo`'nun indeksi) içinde `files` ile belirtilen yollarla tüm dosyaları kaldırın.
