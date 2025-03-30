```
Base.@nospecializeinfer function f(args...)
    @nospecialize ...
    ...
end
Base.@nospecializeinfer f(@nospecialize args...) = ...
```

Derleyiciye `@nospecialize` ile belirtilen argümanların türlerini kullanarak `f`'yi çıkarsamasını söyler. Bu, çıkarım sırasında derleyici tarafından üretilen özel türlerin sayısını sınırlamak için kullanılabilir.

# Örnekler

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline Base.@nospecializeinfer g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Any
└──      return %1
) => Any
```

Bu örnekte, `f` her bir `A` türü için çıkarılacak, ancak `g` yalnızca belirtilen argüman türü `A::AbstractArray` ile bir kez çıkarılacak, bu da derleyicinin bunun üzerinde aşırı çıkarım süresi görmeyeceği anlamına gelir, çünkü bunun somut dönüş türünü çıkaramaz. `@nospecializeinfer` olmadan, `f([1.0])`, `g`'nin dönüş türünü `Float64` olarak çıkarır, bu da çıkarımın `g(::Vector{Float64})` için çalıştığını gösterir, özel kod üretimi yasağına rağmen.

!!! compat "Julia 1.10"
    `Base.@nospecializeinfer` kullanmak Julia sürümü 1.10'u gerektirir.

