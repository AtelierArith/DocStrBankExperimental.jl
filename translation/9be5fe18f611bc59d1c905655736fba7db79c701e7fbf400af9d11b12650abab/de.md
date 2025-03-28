```
crc32c(io::IO, [nb::Integer,] crc::UInt32=0x00000000)
```

Lese bis zu `nb` Bytes von `io` und gebe die CRC-32c-Prüfziffer zurück, optional gemischt mit einer Start-`crc`-Ganzzahl. Wenn `nb` nicht angegeben ist, wird `io` bis zum Ende des Streams gelesen.
