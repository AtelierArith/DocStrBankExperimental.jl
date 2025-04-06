```
OrdinalRange{T, S} <: AbstractRange{T}
```

`T` türünde elemanlara sahip sıralı aralıklar için süpertip. Adımlar her zaman [`oneunit`](@ref) tam katları olmalıdır ve `T` "kesirli" bir tür olmamalıdır; bu tür, `oneunit`'ten daha küçük değerler alamaz. Örneğin, `Integer` veya `Date` türleri uygunken, `Float64` uygun değildir (çünkü bu tür, `oneunit(Float64)`'ten daha küçük değerleri temsil edebilir). [`UnitRange`](@ref), [`StepRange`](@ref) ve diğer türler bunun alt türleridir.
