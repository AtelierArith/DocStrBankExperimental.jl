```
fieldtype(T, name::Symbol | index::Int)
```

Bir bileşik Veri Tipi `T` içindeki bir alanın (isim veya indeks ile belirtilen) beyan edilen türünü belirleyin.

# Örnekler

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtype(Foo, :x)
Int64

julia> fieldtype(Foo, 2)
String
```
