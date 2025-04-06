# SIMD Support

Le type `VecElement{T}` est destiné à la construction de bibliothèques d'opérations SIMD. Son utilisation pratique nécessite l'utilisation de `llvmcall`. Le type est défini comme :

```julia
struct VecElement{T}
    value::T
end
```

Il a une règle de compilation spéciale : un tuple homogène de `VecElement{T}` se mappe à un type `vector` LLVM lorsque `T` est un type de bits primitif.

À `-O3`, le compilateur *pourrait* vectoriser automatiquement les opérations sur de tels tuples. Par exemple, le programme suivant, lorsqu'il est compilé avec `julia -O3`, génère deux instructions d'addition SIMD (`addps`) sur les systèmes x86 :

```julia
const m128 = NTuple{4,VecElement{Float32}}

function add(a::m128, b::m128)
    (VecElement(a[1].value+b[1].value),
     VecElement(a[2].value+b[2].value),
     VecElement(a[3].value+b[3].value),
     VecElement(a[4].value+b[4].value))
end

triple(c::m128) = add(add(c,c),c)

code_native(triple,(m128,))
```

Cependant, comme la vectorisation automatique ne peut pas être fiable, l'utilisation future se fera principalement via des bibliothèques qui utilisent `llvmcall`.
