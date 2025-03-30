```
setfield!(value, name::Symbol, x, [order::Symbol])
setfield!(value, i::Int, x, [order::Symbol])
```

`x`'i, `value`'in adlandırılmış bir alanına atayın. `value` değiştirilebilir olmalı ve `x`, `fieldtype(typeof(value), name)`'in bir alt türü olmalıdır. Ayrıca, bu işlem için bir sıralama belirtilebilir. Alan `@atomic` olarak tanımlandıysa, bu belirtim zorunludur. Aksi takdirde, `@atomic` olarak tanımlanmamışsa, belirtilirse `:not_atomic` olmalıdır. Ayrıca bkz. [`setproperty!`](@ref Base.setproperty!).

# Örnekler

```jldoctest
julia> mutable struct MyMutableStruct
           field::Int
       end

julia> a = MyMutableStruct(1);

julia> setfield!(a, :field, 2);

julia> getfield(a, :field)
2

julia> a = 1//2
1//2

julia> setfield!(a, :num, 3);
HATA: setfield!: değiştirilemez yapı türü Rational değiştirilemez
```
