```
strptime([format], timestr)
```

Biçimlendirilmiş bir zaman dizesini, saniye, dakika, saat, tarih vb. veren bir `TmStruct`'a ayrıştırır. Desteklenen biçimler, standart C kütüphanesindekilerle aynıdır. Bazı platformlarda, zaman dilimleri doğru bir şekilde ayrıştırılmayabilir. Bu işlevin sonucu, epoch'tan itibaren saniyelere dönüştürmek için `time`'a geçirilecekse, `isdst` alanı manuel olarak doldurulmalıdır. Bunu `-1` olarak ayarlamak, C kütüphanesine zaman dilimini belirlemek için mevcut sistem ayarlarını kullanmasını söyleyecektir.
