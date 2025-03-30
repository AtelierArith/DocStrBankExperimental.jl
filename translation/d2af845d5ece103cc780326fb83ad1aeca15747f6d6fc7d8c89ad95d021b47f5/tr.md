```
Pipe()
```

Başka süreçler arasında IO iletişimi için özellikle kullanılmak üzere, başlatılmamış bir Pipe nesnesi oluşturur.

Pipe'ın uygun ucu, nesne süreç oluşturma sırasında kullanıldığında otomatik olarak başlatılacaktır. Bu, süreç boru hatlarında referansları kolayca elde etmek için yararlı olabilir, örneğin:

```
julia> err = Pipe()

# Bu `err` başlatılacak ve `foo`'nun
# stderr'sini `err` borusundan okuyabilirsiniz veya `err`'yi diğer boru hatlarına geçirebilirsiniz.
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)

# Şimdi borunun yazma kısmını yok edin, böylece okuma kısmı EOF alacaktır
julia> closewrite(err)

julia> read(err, String)
"stderr mesajları"
```

Ayrıca [`Base.link_pipe!`](@ref) bakınız.
