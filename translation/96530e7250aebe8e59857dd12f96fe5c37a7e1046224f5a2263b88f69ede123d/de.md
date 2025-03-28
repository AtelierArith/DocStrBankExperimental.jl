```
crc32c(data, crc::UInt32=0x00000000)
```

Berechnen Sie die CRC-32c-Prüfziffer der gegebenen `data`, die ein `Array{UInt8}`, ein zusammenhängendes Teilarray davon oder ein `String` sein kann. Optional können Sie eine Start-`crc`-Ganzzahl übergeben, die mit der Prüfziffer gemischt wird. Der `crc`-Parameter kann verwendet werden, um eine Prüfziffer für Daten zu berechnen, die in Stücke unterteilt sind: `crc32c(data2, crc32c(data1))` entspricht der Prüfziffer von `[data1; data2]`. (Technisch gesehen wird eine little-endian Prüfziffer berechnet.)

Es gibt auch eine Methode `crc32c(io, nb, crc)`, um `nb` Bytes aus einem Stream `io` zu prüfen, oder `crc32c(io, crc)`, um alle verbleibenden Bytes zu prüfen. Daher können Sie [`open(crc32c, filename)`](@ref) verwenden, um eine gesamte Datei zu prüfen, oder `crc32c(seekstart(buf))`, um ein [`IOBuffer`](@ref) zu prüfen, ohne [`take!`](@ref) aufzurufen.

Für einen `String` beachten Sie, dass das Ergebnis spezifisch für die UTF-8-Codierung ist (eine andere Prüfziffer würde aus einer anderen Unicode-Codierung erhalten werden). Um eine Prüfziffer für ein `a::Array` eines anderen Bittyps zu berechnen, können Sie `crc32c(reinterpret(UInt8,a))` verwenden, beachten Sie jedoch, dass das Ergebnis von der Endianness abhängen kann.
