```
withfaces(f, kv::Pair...)
withfaces(f, kvpair_itr)
```

`f`'yi `FACES``.current`'ı sıfır veya daha fazla `:name => val` argümanı `kv` veya `kv`-form değerleri üreten `kvpair_itr` ile geçici olarak değiştirilmiş olarak çalıştırır.

`withfaces` genellikle `withfaces(kv...) do ... end` sözdizimi aracılığıyla kullanılır. `nothing` değeri, bir yüz geçici olarak sıfırlamak için kullanılabilir (eğer ayarlanmışsa). `withfaces` döndüğünde, orijinal `FACES``.current` geri yüklenmiştir.

# Örnekler

```jldoctest; setup = :(import StyledStrings: Face, withfaces)
julia> withfaces(:yellow => Face(foreground=:red), :green => :blue) do
           println(styled"{yellow:red} ve {green:blue} karışımı {magenta:purple} yapar")
       end
kırmızı ve mavi karışımı mor yapar
```
