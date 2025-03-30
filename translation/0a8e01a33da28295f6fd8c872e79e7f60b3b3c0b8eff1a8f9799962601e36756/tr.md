```
TCPSocket(; delay=true)
```

libuv kullanarak bir TCP soketi açar. Eğer `delay` true ise, libuv soketin dosya tanımlayıcısının oluşturulmasını ilk [`bind`](@ref) çağrısına kadar geciktirir. `TCPSocket`, soketin durumunu ve gönderme/alma tamponlarını belirtmek için çeşitli alanlara sahiptir.
