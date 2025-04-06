```
@Kwargs{key1::Type1, key2::Type2, ...}
```

Dieses Makro bietet eine bequeme Möglichkeit, die Typdarstellung von Schlüsselwortargumenten aus derselben Syntax wie [`@NamedTuple`](@ref) zu erstellen. Zum Beispiel, wenn wir einen Funktionsaufruf wie `func([positional arguments]; kw1=1.0, kw2="2")` haben, können wir dieses Makro verwenden, um die interne Typdarstellung der Schlüsselwortargumente als `@Kwargs{kw1::Float64, kw2::String}` zu konstruieren. Die Makrosyntax ist speziell darauf ausgelegt, den Signaturtyp einer Schlüsselwortmethode zu vereinfachen, wenn sie in der Stack-Trace-Ansicht gedruckt wird.

```julia
julia> @Kwargs{init::Int} # die interne Darstellung von Schlüsselwortargumenten
Base.Pairs{Symbol, Int64, Tuple{Symbol}, @NamedTuple{init::Int64}}

julia> sum("julia"; init=1)
ERROR: MethodError: kein passender Methode für +(::Char, ::Char) gefunden
Die Funktion `+` existiert, aber keine Methode ist für diese Kombination von Argumenttypen definiert.

Nächste Kandidaten sind:
  +(::Any, ::Any, ::Any, ::Any...)
   @ Base operators.jl:585
  +(::Integer, ::AbstractChar)
   @ Base char.jl:247
  +(::T, ::Integer) wo T<:AbstractChar
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
    Dieses Makro ist seit Julia 1.10 verfügbar.

