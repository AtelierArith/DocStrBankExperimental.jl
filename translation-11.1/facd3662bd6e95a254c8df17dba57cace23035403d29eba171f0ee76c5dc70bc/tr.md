```
SimpleLogger([stream,] min_level=Info)
```

`min_level`'e eşit veya daha büyük seviyedeki tüm mesajları `stream`'e kaydeden basit bir günlüğü kaydedici. Eğer akış kapalıysa, `Warn` seviyesinden büyük veya eşit olan mesajlar `stderr`'ye, daha düşük seviyedekiler ise `stdout`'ya kaydedilecektir.
