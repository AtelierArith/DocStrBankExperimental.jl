```
@Kwargs{key1::Type1, key2::Type2, ...}
```

Ce macro offre un moyen pratique de construire la représentation de type des arguments de mot-clé à partir de la même syntaxe que [`@NamedTuple`](@ref). Par exemple, lorsque nous avons un appel de fonction comme `func([arguments positionnels]; kw1=1.0, kw2="2")`, nous pouvons utiliser ce macro pour construire la représentation interne de type des arguments de mot-clé comme `@Kwargs{kw1::Float64, kw2::String}`. La syntaxe du macro est spécifiquement conçue pour simplifier le type de signature d'une méthode de mot-clé lorsqu'elle est imprimée dans la vue de trace de pile.

```julia
julia> @Kwargs{init::Int} # la représentation interne des arguments de mot-clé
Base.Pairs{Symbol, Int64, Tuple{Symbol}, @NamedTuple{init::Int64}}

julia> sum("julia"; init=1)
ERROR: MethodError: no method matching +(::Char, ::Char)
La fonction `+` existe, mais aucune méthode n'est définie pour cette combinaison de types d'arguments.

Les candidats les plus proches sont :
  +(::Any, ::Any, ::Any, ::Any...)
   @ Base operators.jl:585
  +(::Integer, ::AbstractChar)
   @ Base char.jl:247
  +(::T, ::Integer) où T<:AbstractChar
   @ Base char.jl:237

Trace de la pile :
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
    Ce macro est disponible depuis Julia 1.10.

