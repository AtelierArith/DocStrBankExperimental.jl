```
crc32c(io::IO, [nb::Integer,] crc::UInt32=0x00000000)
```

Lee hasta `nb` bytes de `io` y devuelve el checksum CRC-32c, opcionalmente mezclado con un entero `crc` inicial. Si `nb` no se proporciona, entonces `io` se leerá hasta el final del flujo.
