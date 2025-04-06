```
@Kwargs{key1::Type1, key2::Type2, ...}
```

Este macro proporciona una forma conveniente de construir la representación de tipo de argumentos de palabra clave a partir de la misma sintaxis que [`@NamedTuple`](@ref). Por ejemplo, cuando tenemos una llamada a función como `func([argumentos posicionales]; kw1=1.0, kw2="2")`, podemos usar este macro para construir la representación interna de tipo de los argumentos de palabra clave como `@Kwargs{kw1::Float64, kw2::String}`. La sintaxis del macro está diseñada específicamente para simplificar el tipo de firma de un método de palabra clave cuando se imprime en la vista de traza de pila.

```julia
julia> @Kwargs{init::Int} # la representación interna de los argumentos de palabra clave
Base.Pairs{Symbol, Int64, Tuple{Symbol}, @NamedTuple{init::Int64}}

julia> sum("julia"; init=1)
ERROR: MethodError: no method matching +(::Char, ::Char)
La función `+` existe, pero no se define ningún método para esta combinación de tipos de argumento.

Los candidatos más cercanos son:
  +(::Any, ::Any, ::Any, ::Any...)
   @ Base operators.jl:585
  +(::Integer, ::AbstractChar)
   @ Base char.jl:247
  +(::T, ::Integer) where T<:AbstractChar
   @ Base char.jl:237

Stacktrace:
  [1] add_sum(x::Char, y::Char)
    @ Base ./reduce.jl:24
  [2] BottomRF
    @ Base ./reduce.jl:86 [inlined]
  [3] _foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, init::Int64, itr::String)
    @ Base ./reduce.jl:62
  [4] foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, nt::Int64, itr::String)
    @ Base ./reduce.jl:48 [inlined]
  [5] mapfoldl_impl(f::typeof(identity), op::typeof(Base.add_sum), nt::Int64, itr::String)
    @ Base ./reduce.jl:44 [inlined]
  [6] mapfoldl(f::typeof(identity), op::typeof(Base.add_sum), itr::String; init::Int64)
    @ Base ./reduce.jl:175 [inlined]
  [7] mapreduce(f::typeof(identity), op::typeof(Base.add_sum), itr::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:307 [inlined]
  [8] sum(f::typeof(identity), a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:535 [inlined]
  [9] sum(a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:564 [inlined]
 [10] top-level scope
    @ REPL[12]:1
```

!!! compat "Julia 1.10"
    Este macro está disponible a partir de Julia 1.10.

