```
fill(value, dims::Tuple)
fill(value, dims...)
```

Boyutları `dims` olan ve her konumu `value` ile ayarlanmış bir dizi oluşturur.

Örneğin, `fill(1.0, (5,5))` her konumunda `1.0` bulunan 5×5'lik bir float dizisi döndürür.

Boyut uzunlukları `dims` ya bir demet (tuple) ya da bir argüman dizisi olarak belirtilebilir. `value`'dan sonra gelen `N` uzunluğundaki bir demet veya `N` argümanı, `N`-boyutlu bir dizi belirtir. Bu nedenle, yalnızca `x` ile ayarlanmış sıfır-boyutlu bir dizi oluşturmak için yaygın bir deyim `fill(x)`'dir.

Döndürülen dizinin her konumu, geçilen `value` ile ayarlanmıştır (ve dolayısıyla [`===`](@ref) ile eşittir); bu, eğer `value` kendisi değiştirilirse, `fill` edilmiş dizinin tüm elemanlarının bu değişikliği yansıtacağı anlamına gelir çünkü hala o `value`'dur. Bu, `fill(1.0, (5,5))` ile bir sorun değildir çünkü `value` olan `1.0` değiştirilemez ve kendisi değiştirilemez, ancak genellikle diziler gibi değiştirilebilir değerlerle beklenmedik olabilir. Örneğin, `fill([], 3)` döndürülen vektörün üç konumuna *tam olarak aynı* boş diziyi yerleştirir:

```jldoctest
julia> v = fill([], 3)
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v[1] === v[2] === v[3]
true

julia> value = v[1]
Any[]

julia> push!(value, 867_5309)
1-element Vector{Any}:
 8675309

julia> v
3-element Vector{Vector{Any}}:
 [8675309]
 [8675309]
 [8675309]
```

Birçok bağımsız iç dizi oluşturmak için bunun yerine bir [kapsam](@ref man-comprehensions) kullanın. Bu, döngünün her yinelemesinde yeni ve ayrı bir dizi oluşturur:

```jldoctest
julia> v2 = [[] for _ in 1:3]
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v2[1] === v2[2] === v2[3]
false

julia> push!(v2[1], 8675309)
1-element Vector{Any}:
 8675309

julia> v2
3-element Vector{Vector{Any}}:
 [8675309]
 []
 []
```

Ayrıca bakınız: [`fill!`](@ref), [`zeros`](@ref), [`ones`](@ref), [`similar`](@ref).

# Örnekler

```jldoctest
julia> fill(1.0, (2,3))
2×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> fill(42)
0-boyutlu Array{Int64, 0}:
42

julia> A = fill(zeros(2), 2) # her iki elemanı da aynı [0.0, 0.0] vektörüne ayarlar
2-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 0.0]

julia> A[1][1] = 42; # doldurulmuş değeri [42.0, 0.0] olarak değiştirir

julia> A # hem A[1] hem de A[2] tam olarak aynı vektördür
2-element Vector{Vector{Float64}}:
 [42.0, 0.0]
 [42.0, 0.0]
```
