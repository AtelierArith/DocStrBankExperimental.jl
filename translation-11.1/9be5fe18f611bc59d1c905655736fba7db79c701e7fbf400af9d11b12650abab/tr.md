```
crc32c(io::IO, [nb::Integer,] crc::UInt32=0x00000000)
```

`io`'dan `nb` bayta kadar oku ve isteğe bağlı olarak başlangıç `crc` tam sayısı ile karıştırılmış CRC-32c kontrol toplamını döndür. Eğer `nb` sağlanmazsa, `io` akışın sonuna kadar okunacaktır.
