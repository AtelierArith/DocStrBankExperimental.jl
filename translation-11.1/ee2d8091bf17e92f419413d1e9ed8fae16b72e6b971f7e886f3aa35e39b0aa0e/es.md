# SIMD Support

El tipo `VecElement{T}` está destinado a construir bibliotecas de operaciones SIMD. El uso práctico de este requiere utilizar `llvmcall`. El tipo se define como:

```julia
struct VecElement{T}
    value::T
end
```

Tiene una regla de compilación especial: un tuple homogéneo de `VecElement{T}` se mapea a un tipo `vector` de LLVM cuando `T` es un tipo de bits primitivo.

En `-O3`, el compilador *podría* vectorizar automáticamente las operaciones en tales tuplas. Por ejemplo, el siguiente programa, cuando se compila con `julia -O3`, genera dos instrucciones de suma SIMD (`addps`) en sistemas x86:

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

Sin embargo, dado que no se puede confiar en la vectorización automática, el uso futuro será principalmente a través de bibliotecas que utilicen `llvmcall`.
