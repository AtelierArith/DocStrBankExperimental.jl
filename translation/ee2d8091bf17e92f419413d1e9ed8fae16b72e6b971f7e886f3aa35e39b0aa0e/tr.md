# SIMD Support

`VecElement{T}` türü, SIMD işlemleri kütüphaneleri oluşturmak için tasarlanmıştır. Pratik kullanımı `llvmcall` kullanmayı gerektirir. Tür şu şekilde tanımlanmıştır:

```julia
struct VecElement{T}
    value::T
end
```

Özel bir derleme kuralı vardır: `VecElement{T}`'nin homojen bir demeti, `T` bir ilkel bit türü olduğunda bir LLVM `vector` türüne eşlenir.

`-O3` ile derlendiğinde, derleyici bu tür demetler üzerindeki işlemleri otomatik olarak vektörleştirebilir. Örneğin, aşağıdaki program `julia -O3` ile derlendiğinde, x86 sistemlerinde iki SIMD toplama talimatı (`addps`) üretir:

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

Ancak, otomatik vektörlemenin güvenilir olmaması nedeniyle, gelecekteki kullanım çoğunlukla `llvmcall` kullanan kütüphaneler aracılığıyla olacaktır.
