```
@Kwargs{key1::Type1, key2::Type2, ...}
```

Bu makro, [`@NamedTuple`](@ref) ile aynı sözdiziminden anahtar argümanların tür temsilini oluşturmanın pratik bir yolunu sağlar. Örneğin, `func([positional arguments]; kw1=1.0, kw2="2")` gibi bir fonksiyon çağrımız olduğunda, bu makroyu kullanarak anahtar argümanların iç tür temsilini `@Kwargs{kw1::Float64, kw2::String}` olarak oluşturabiliriz. Makro sözdizimi, bir anahtar yönteminin imza türünü yığın izleme görünümünde basıldığında basitleştirmek için özel olarak tasarlanmıştır.

```julia
julia> @Kwargs{init::Int} # anahtar argümanların iç temsil
Base.Pairs{Symbol, Int64, Tuple{Symbol}, @NamedTuple{init::Int64}}

julia> sum("julia"; init=1)
HATA: MethodError: +(::Char, ::Char) için eşleşen bir yöntem yok
`+` fonksiyonu mevcut, ancak bu argüman türleri kombinasyonu için tanımlı bir yöntem yok.

En yakın adaylar:
  +(::Any, ::Any, ::Any, ::Any...)
   @ Base operators.jl:585
  +(::Integer, ::AbstractChar)
   @ Base char.jl:247
  +(::T, ::Integer) where T<:AbstractChar
   @ Base char.jl:237

Yığın izi:
  [1] add_sum(x::Char, y::Char)
    @ Base ./reduce.jl:24
  [2] BottomRF
    @ Base ./reduce.jl:86 [iç içe]
  [3] _foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, init::Int64, itr::String)
    @ Base ./reduce.jl:62
  [4] foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, nt::Int64, itr::String)
    @ Base ./reduce.jl:48 [iç içe]
  [5] mapfoldl_impl(f::typeof(identity), op::typeof(Base.add_sum), nt::Int64, itr::String)
    @ Base ./reduce.jl:44 [iç içe]
  [6] mapfoldl(f::typeof(identity), op::typeof(Base.add_sum), itr::String; init::Int64)
    @ Base ./reduce.jl:175 [iç içe]
  [7] mapreduce(f::typeof(identity), op::typeof(Base.add_sum), itr::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:307 [iç içe]
  [8] sum(f::typeof(identity), a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:535 [iç içe]
  [9] sum(a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:564 [iç içe]
 [10] üst düzey kapsam
    @ REPL[12]:1
```

!!! compat "Julia 1.10"
    Bu makro, Julia 1.10 itibarıyla mevcuttur.

