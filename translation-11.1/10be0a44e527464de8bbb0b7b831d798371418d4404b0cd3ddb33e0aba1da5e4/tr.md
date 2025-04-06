```
=
```

`=` atama operatörüdür.

  * Değişken `a` ve ifade `b` için, `a = b` ifadesi `a`nın `b`nin değerine referans vermesini sağlar.
  * Fonksiyonlar `f(x)` için, `f(x) = x` yeni bir fonksiyon sabiti `f` tanımlar veya `f` zaten tanımlıysa `f`ye yeni bir yöntem ekler; bu kullanım `function f(x); x; end` ile eşdeğerdir.
  * `a[i] = v` [`setindex!`](@ref)`(a,v,i)` çağrısını yapar.
  * `a.b = c` [`setproperty!`](@ref)`(a,:b,c)` çağrısını yapar.
  * Bir fonksiyon çağrısı içinde, `f(a=b)` `b`yi anahtar argüman `a`nın değeri olarak geçirir.
  * Virgüllerle birlikte parantez içinde, `(a=1,)` bir [`NamedTuple`](@ref) oluşturur.

# Örnekler

`a`yı `b`ye atamak `b`nin bir kopyasını oluşturmaz; bunun yerine [`copy`](@ref) veya [`deepcopy`](@ref) kullanın.

```jldoctest
julia> b = [1]; a = b; b[1] = 2; a
1-element Array{Int64, 1}:
 2

julia> b = [1]; a = copy(b); b[1] = 2; a
1-element Array{Int64, 1}:
 1

```

Fonksiyonlara geçirilen koleksiyonlar da kopyalanmaz. Fonksiyonlar, argümanlarının referans verdiği nesnelerin içeriğini değiştirebilir (mutate edebilir). (Bunu yapan fonksiyonların isimleri geleneksel olarak '!' ile sonlandırılır.)

```jldoctest
julia> function f!(x); x[:] .+= 1; end
f! (generic function with 1 method)

julia> a = [1]; f!(a); a
1-element Array{Int64, 1}:
 2

```

Atama, bir iterable'dan değer alarak birden fazla değişken üzerinde paralel olarak çalışabilir:

```jldoctest
julia> a, b = 4, 5
(4, 5)

julia> a, b = 1:3
1:3

julia> a, b
(1, 2)

```

Atama, birden fazla değişken üzerinde ardışık olarak çalışabilir ve sağdaki en sağdaki ifadenin değerini döndürür:

```jldoctest
julia> a = [1]; b = [2]; c = [3]; a = b = c
1-element Array{Int64, 1}:
 3

julia> b[1] = 2; a, b, c
([2], [2], [2])

```

Sınır dışı indekslerde atama, bir koleksiyonu büyütmez. Eğer koleksiyon bir [`Vector`](@ref) ise, bunun yerine [`push!`](@ref) veya [`append!`](@ref) ile büyütülebilir.

```jldoctest
julia> a = [1, 1]; a[3] = 2
HATA: BoundsError: 2-element Array{Int64, 1} at index [3] erişim denemesi
[...]

julia> push!(a, 2, 3)
4-element Array{Int64, 1}:
 1
 1
 2
 3

```

`[]` atamak bir koleksiyondan elemanları ortadan kaldırmaz; bunun yerine [`filter!`](@ref) kullanın.

```jldoctest
julia> a = collect(1:3); a[a .<= 1] = []
HATA: DimensionMismatch: 1 hedefe 0 eleman atamaya çalışıldı
[...]

julia> filter!(x -> x > 1, a) # yerinde & dolayısıyla a = a[a .> 1] den daha verimli
2-element Array{Int64, 1}:
 2
 3

```
