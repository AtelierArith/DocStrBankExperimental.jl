```
crc32c(data, crc::UInt32=0x00000000)
```

Calculez le checksum CRC-32c des données données, qui peuvent être un `Array{UInt8}`, un sous-tableau contigu de celui-ci, ou une `String`. En option, vous pouvez passer un entier `crc` de départ à mélanger avec le checksum. Le paramètre `crc` peut être utilisé pour calculer un checksum sur des données divisées en morceaux : effectuer `crc32c(data2, crc32c(data1))` est équivalent au checksum de `[data1; data2]`. (Techniquement, un checksum en little-endian est calculé.)

Il existe également une méthode `crc32c(io, nb, crc)` pour calculer le checksum de `nb` octets à partir d'un flux `io`, ou `crc32c(io, crc)` pour calculer le checksum de tous les octets restants. Ainsi, vous pouvez faire [`open(crc32c, filename)`](@ref) pour calculer le checksum d'un fichier entier, ou `crc32c(seekstart(buf))` pour calculer le checksum d'un [`IOBuffer`](@ref) sans appeler [`take!`](@ref).

Pour une `String`, notez que le résultat est spécifique à l'encodage UTF-8 (un checksum différent serait obtenu à partir d'un autre encodage Unicode). Pour calculer le checksum d'un `a::Array` d'un autre type de bits, vous pouvez faire `crc32c(reinterpret(UInt8,a))`, mais notez que le résultat peut dépendre de l'endianness.
