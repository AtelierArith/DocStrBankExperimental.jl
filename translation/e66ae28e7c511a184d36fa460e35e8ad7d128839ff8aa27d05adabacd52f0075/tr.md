```
ComposedFunction{Outer,Inner} <: Function
```

İki çağrılabilir nesnenin `outer::Outer` ve `inner::Inner` bileşimini temsil eder. Yani

```julia
ComposedFunction(outer, inner)(args...; kw...) === outer(inner(args...; kw...))
```

Bir `ComposedFunction` örneği oluşturmanın tercih edilen yolu bileşim operatörünü [`∘`](@ref) kullanmaktır:

```jldoctest
julia> sin ∘ cos === ComposedFunction(sin, cos)
true

julia> typeof(sin∘cos)
ComposedFunction{typeof(sin), typeof(cos)}
```

Bileşen parçaları `ComposedFunction`'ın alanlarında saklanır ve aşağıdaki gibi alınabilir:

```jldoctest
julia> composition = sin ∘ cos
sin ∘ cos

julia> composition.outer === sin
true

julia> composition.inner === cos
true
```

!!! compat "Julia 1.6"
    ComposedFunction en az Julia 1.6 gerektirir. Önceki sürümlerde `∘` anonim bir fonksiyon döndürür.


Ayrıca bkz. [`∘`](@ref).
