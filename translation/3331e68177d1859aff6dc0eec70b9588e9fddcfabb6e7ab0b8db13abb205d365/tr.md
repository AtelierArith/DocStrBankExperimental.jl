```
displaysize([io::IO]) -> (satırlar, sütunlar)
```

Bu `IO` nesnesine çıktı render etmek için kullanılabilecek ekranın nominal boyutunu döndürür. Hiçbir girdi sağlanmazsa, ortam değişkenleri `LINES` ve `COLUMNS` okunur. Eğer bunlar ayarlanmamışsa, varsayılan boyut olarak `(24, 80)` döndürülür.

# Örnekler

```jldoctest
julia> withenv("LINES" => 30, "COLUMNS" => 100) do
           displaysize()
       end
(30, 100)
```

TTY boyutunuzu almak için,

```julia-repl
julia> displaysize(stdout)
(34, 147)
```
