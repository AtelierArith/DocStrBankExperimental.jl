```
struct
```

Julia'da en yaygın kullanılan tür, bir ad ve bir dizi alan ile belirtilen bir struct'tır.

```julia
struct Point
    x
    y
end
```

Alanların tür kısıtlamaları olabilir ve bu kısıtlamalar parametreli olabilir:

```julia
struct Point{X}
    x::X
    y::Float64
end
```

Bir struct ayrıca `<:` sözdizimi ile soyut bir üst türü de ilan edebilir:

```julia
struct Point <: AbstractPoint
    x
    y
end
```

`struct`'lar varsayılan olarak değiştirilemez; bu türlerden birinin bir örneği inşa edildikten sonra değiştirilemez. Değiştirilebilir örneklere sahip bir tür tanımlamak için [`mutable struct`](@ref) kullanın.

Yapıcıları nasıl tanımlayacağınız gibi daha fazla ayrıntı için [Bileşik Türler](@ref) bölümüne bakın.
