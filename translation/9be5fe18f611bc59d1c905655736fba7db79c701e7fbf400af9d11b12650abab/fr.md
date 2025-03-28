```
crc32c(io::IO, [nb::Integer,] crc::UInt32=0x00000000)
```

Lire jusqu'à `nb` octets de `io` et retourner le checksum CRC-32c, éventuellement mélangé avec un entier `crc` de départ. Si `nb` n'est pas fourni, alors `io` sera lu jusqu'à la fin du flux.
