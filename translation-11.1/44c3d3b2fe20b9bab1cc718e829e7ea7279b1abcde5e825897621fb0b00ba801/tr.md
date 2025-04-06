```
nagle(socket::Union{TCPServer, TCPSocket}, enable::Bool)
```

Nagle algoritması, birden fazla küçük TCP paketini daha büyük olanlar halinde toplar. Bu, verimliliği artırabilir ancak gecikmeyi kötüleştirebilir. Nagle algoritması varsayılan olarak etkindir. Bu fonksiyon, belirli bir TCP sunucusunda veya soketinde Nagle algoritmasının aktif olup olmadığını ayarlar. Karşıt seçenek, diğer dillerde `TCP_NODELAY` olarak adlandırılır.

!!! compat "Julia 1.3"
    Bu fonksiyon, Julia 1.3 veya daha yenisini gerektirir.

