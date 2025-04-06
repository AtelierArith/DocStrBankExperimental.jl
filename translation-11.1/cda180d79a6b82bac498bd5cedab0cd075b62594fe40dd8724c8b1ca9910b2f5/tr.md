```
Tuple{Types...}
```

Bir tuple, farklı türlerdeki herhangi bir değeri tutabilen sabit uzunlukta bir konteynerdir, ancak değiştirilemez (değişmez). Değerlere indeksleme ile erişilebilir. Tuple literalleri virgüller ve parantezler ile yazılır:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"

julia> typeof(x)
Tuple{Float64, String, Int64}
```

Uzunluğu 1 olan bir tuple, bir virgül ile yazılmalıdır, `(1,)`, çünkü `(1)` sadece parantez içine alınmış bir değerdir. `()` boş (uzunluğu 0) tuple'ı temsil eder.

Bir tuple, bir `Tuple` türü kullanılarak bir iterator'dan oluşturulabilir:

```jldoctest
julia> Tuple(["a", 1])
("a", 1)

julia> Tuple{String, Float64}(["a", 1])
("a", 1.0)
```

Tuple türleri, parametrelerinde kovaryandır: `Tuple{Int}` bir `Tuple{Any}` alt türüdür. Bu nedenle `Tuple{Any}` soyut bir tür olarak kabul edilir ve tuple türleri yalnızca parametreleri somut olduğunda somut hale gelir. Tuple'lar alan adlarına sahip değildir; alanlara yalnızca indeks ile erişilir. Tuple türleri herhangi bir sayıda parametreye sahip olabilir.

[Tuple Types](@ref) bölümüne bakın.

Ayrıca [`Vararg`](@ref), [`NTuple`](@ref), [`ntuple`](@ref), [`tuple`](@ref), [`NamedTuple`](@ref) ile ilgili daha fazla bilgiye bakın.
