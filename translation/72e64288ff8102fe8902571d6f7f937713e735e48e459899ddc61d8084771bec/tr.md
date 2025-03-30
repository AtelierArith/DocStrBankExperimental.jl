```
for outer
```

Bir `for` döngüsünde yineleme için mevcut bir yerel değişkeni yeniden kullanın.

Daha fazla bilgi için [değişken kapsamı ile ilgili kılavuz bölümüne](@ref scope-of-variables) bakın.

Ayrıca [`for`](@ref) bölümüne de bakın.

# Örnekler

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # boş
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # boş
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # global değişken
       for outer i = 1:3
       end
HATA: sözdizimi: "for outer" için dış yerel değişken bildirimi yok
[...]
```
