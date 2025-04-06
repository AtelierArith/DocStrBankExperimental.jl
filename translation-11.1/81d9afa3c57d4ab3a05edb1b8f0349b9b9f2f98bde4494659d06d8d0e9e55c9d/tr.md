```
ScopedValue(x)
```

Dinamik kapsamlar arasında değerleri yaymak için bir konteyner oluşturun. Yeni bir dinamik kapsam oluşturmak ve girmek için [`with`](@ref) kullanın.

Değerler yalnızca yeni bir dinamik kapsam içine girerken ayarlanabilir ve referans verilen değer, bir dinamik kapsamın yürütülmesi sırasında sabit kalacaktır.

Dinamik kapsamlar görevler arasında yayılır.

# Örnekler

```jldoctest
julia> using Base.ScopedValues;

julia> const sval = ScopedValue(1);

julia> sval[]
1

julia> with(sval => 2) do
           sval[]
       end
2

julia> sval[]
1
```

!!! compat "Julia 1.11"
    Scoped values, Julia 1.11'de tanıtılmıştır. Julia 1.8+ sürümünde uyumlu bir uygulama ScopedValues.jl paketinden mevcuttur.

