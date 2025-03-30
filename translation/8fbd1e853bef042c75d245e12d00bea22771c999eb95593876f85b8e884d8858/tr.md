```
fieldtypes(T::Type)
```

Bir bileşik DataType `T` içindeki tüm alanların belirtilen türlerini bir demet olarak döndürür.

!!! compat "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> struct Foo
           x::Int64
           y::String
       end

julia> fieldtypes(Foo)
(Int64, String)
```
