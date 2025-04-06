# SIMD Support

Der Typ `VecElement{T}` ist für den Aufbau von Bibliotheken für SIMD-Operationen vorgesehen. Praktische Anwendungen erfordern die Verwendung von `llvmcall`. Der Typ ist definiert als:

```julia
struct VecElement{T}
    value::T
end
```

Es hat eine spezielle Kompilierungsregel: Ein homogene Tupel von `VecElement{T}` wird auf einen LLVM `vector`-Typ abgebildet, wenn `T` ein primitiver Bits-Typ ist.

Bei `-O3` könnte der Compiler *automatisch* Operationen auf solchen Tupeln vektorisieren. Zum Beispiel erzeugt das folgende Programm, wenn es mit `julia -O3` kompiliert wird, zwei SIMD-Additionsanweisungen (`addps`) auf x86-Systemen:

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

Allerdings kann die automatische Vektorisierung nicht darauf vertraut werden, sodass die zukünftige Nutzung hauptsächlich über Bibliotheken erfolgen wird, die `llvmcall` verwenden.
