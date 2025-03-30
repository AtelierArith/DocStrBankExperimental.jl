```
crc32c(data, crc::UInt32=0x00000000)
```

Verilen `data`'nın CRC-32c kontrol toplamını hesaplar; bu `Array{UInt8}`, bunun bir bitişik alt dizisi veya bir `String` olabilir. İsteğe bağlı olarak, kontrol toplamı ile karıştırılacak bir başlangıç `crc` tam sayısı geçebilirsiniz. `crc` parametresi, verileri parçalara ayırarak bir kontrol toplamı hesaplamak için kullanılabilir: `crc32c(data2, crc32c(data1))` ifadesi, `[data1; data2]`'nin kontrol toplamına eşdeğerdir. (Teknik olarak, bir little-endian kontrol toplamı hesaplanır.)

Bir akış `io`'dan `nb` baytını kontrol toplamı hesaplamak için `crc32c(io, nb, crc)` yöntemi veya kalan tüm baytları kontrol toplamı hesaplamak için `crc32c(io, crc)` yöntemi de vardır. Bu nedenle, tüm bir dosyanın kontrol toplamını hesaplamak için [`open(crc32c, filename)`](@ref) yapabilir veya [`take!`](@ref) çağırmadan bir [`IOBuffer`](@ref) için kontrol toplamı hesaplamak için `crc32c(seekstart(buf))` yapabilirsiniz.

Bir `String` için, sonucun UTF-8 kodlamasına özgü olduğunu unutmayın (farklı bir Unicode kodlamasından farklı bir kontrol toplamı elde edilir). Başka bir bit türüne sahip bir `a::Array` için kontrol toplamı hesaplamak istiyorsanız, `crc32c(reinterpret(UInt8,a))` yapabilirsiniz, ancak sonucun endian bağımlı olabileceğini unutmayın.
