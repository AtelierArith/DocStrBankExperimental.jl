```
Serialization.writeheader(s::AbstractSerializer)
```

Schreiben Sie einen identifizierenden Header in den angegebenen Serializer. Der Header besteht aus 8 Bytes wie folgt:

| Offset | Beschreibung                                |
|:------ |:------------------------------------------- |
| 0      | Tag-Byte (0x37)                             |
| 1-2    | Signatur-Bytes "JL"                         |
| 3      | Protokollversion                            |
| 4      | Bits 0-1: Endianness: 0 = little, 1 = big   |
| 4      | Bits 2-3: Plattform: 0 = 32-Bit, 1 = 64-Bit |
| 5-7    | reserviert                                  |
