```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

Küresel bir değişkenin veya nesne alanının tanımlı olup olmadığını test eder. Argümanlar bir modül ve bir sembol veya bir bileşik nesne ve alan adı (sembol olarak) veya indeks olabilir. İsteğe bağlı olarak, işlem için bir sıralama tanımlanabilir. Alan `@atomic` olarak tanımlandıysa, spesifikasyonun o konuma yapılan depolamalarla uyumlu olması şiddetle önerilir. Aksi takdirde, `@atomic` olarak tanımlanmamışsa, belirtilirse bu parametre `:not_atomic` olmalıdır.

Bir dizi elemanının tanımlı olup olmadığını test etmek için [`isassigned`](@ref) kullanın.

Ayrıca [`@isdefined`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
