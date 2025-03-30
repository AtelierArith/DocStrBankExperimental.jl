```
getfield(value, name::Symbol, [order::Symbol])
getfield(value, i::Int, [order::Symbol])
```

Bir bileşen `value`'dan isim veya pozisyona göre bir alan çıkarın. İsteğe bağlı olarak, işlem için bir sıralama tanımlanabilir. Alan `@atomic` olarak tanımlandıysa, spesifikasyonın o konumdaki depolamalarla uyumlu olması şiddetle önerilir. Aksi takdirde, `@atomic` olarak tanımlanmamışsa, bu parametre belirtilirse `:not_atomic` olmalıdır. Ayrıca [`getproperty`](@ref Base.getproperty) ve [`fieldnames`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> a = 1//2
1//2

julia> getfield(a, :num)
1

julia> a.num
1

julia> getfield(a, 1)
1
```
