```
Base.isambiguous(m1, m2; ambiguous_bottom=false) -> Bool
```

İki yöntem `m1` ve `m2`'nin bazı çağrı imzaları için belirsiz olup olmadığını belirleyin. Bu test, aynı işlevin diğer yöntemleri bağlamında gerçekleştirilir; izole olarak, `m1` ve `m2` belirsiz olabilir, ancak belirsizliği çözen üçüncü bir yöntem tanımlanmışsa, bu `false` döner. Alternatif olarak, izole olarak `m1` ve `m2` sıralanabilir, ancak üçüncü bir yöntem bunlarla sıralanamazsa, birlikte bir belirsizlik yaratabilirler.

Parametrik türler için, `ambiguous_bottom` anahtar kelime argümanı `Union{}`'nin tür parametrelerinin belirsiz bir kesişimi olarak sayılıp sayılmayacağını kontrol eder - `true` olduğunda belirsiz olarak kabul edilir, `false` olduğunda edilmez.

# Örnekler

```jldoctest
julia> foo(x::Complex{<:Integer}) = 1
foo (generic function with 1 method)

julia> foo(x::Complex{<:Rational}) = 2
foo (generic function with 2 methods)

julia> m1, m2 = collect(methods(foo));

julia> typeintersect(m1.sig, m2.sig)
Tuple{typeof(foo), Complex{Union{}}}

julia> Base.isambiguous(m1, m2, ambiguous_bottom=true)
true

julia> Base.isambiguous(m1, m2, ambiguous_bottom=false)
false
```
