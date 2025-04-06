```
closewrite(stream)
```

Tam çift yönlü bir G/Ç akışının yazma kısmını kapatır. Öncelikle bir [`flush`](@ref) gerçekleştirir. Diğer uca, altta yatan dosyaya daha fazla veri yazılmayacağını bildirir. Bu, tüm G/Ç türleri tarafından desteklenmez.

Eğer uygulanmışsa, `closewrite`, engellenmesi gereken sonraki `read` veya `eof` çağrılarının yerine EOF fırlatmasına veya sırasıyla true döndürmesine neden olur. Eğer akış zaten kapatılmışsa, bu idempotenttir.

# Örnekler

```jldoctest
julia> io = Base.BufferStream(); # bu asla engellenmez, bu yüzden aynı Görev üzerinde okuyabilir ve yazabiliriz

julia> write(io, "request");

julia> # burada `read(io)` çağrısı sonsuza kadar engellenecektir

julia> closewrite(io);

julia> read(io, String)
"request"
```
