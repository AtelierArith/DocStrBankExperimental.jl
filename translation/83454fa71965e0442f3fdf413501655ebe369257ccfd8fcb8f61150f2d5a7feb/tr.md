```
norm(A, p::Real=2)
```

Herhangi bir sayılar (veya `norm`'un tanımlı olduğu herhangi bir eleman türü) içeren `A` adlı iterable konteyner için, `A`'yı ilgili uzunluktaki bir vektör gibi kabul ederek `p`-normunu (varsayılan olarak `p=2`) hesaplayın.

`p`-normu şu şekilde tanımlanır:

$$
\|A\|_p = \left( \sum_{i=1}^n | a_i | ^p \right)^{1/p}
$$

burada $a_i$ `A`'nın elemanları, $| a_i |$ `a_i`'nin [`norm`](@ref) değeri ve $n$ `A`'nın uzunluğudur. `p`-normu, `A`'nın elemanlarının [`norm`](@ref) değerleri kullanılarak hesaplandığı için, `p != 2` olduğunda bir vektörler vektörünün `p`-normu, genel olarak bir blok vektör olarak yorumlanmasıyla uyumlu değildir.

`p`, herhangi bir sayısal değeri alabilir (her ne kadar tüm değerler matematiksel olarak geçerli bir vektör normu üretmese de). Özellikle, `norm(A, Inf)` `abs.(A)` içindeki en büyük değeri döndürürken, `norm(A, -Inf)` en küçük değeri döndürür. Eğer `A` bir matris ise ve `p=2` ise, bu Frobenius normuna eşdeğerdir.

İkinci argüman `p`, `norm` arayüzünün bir parçası olmak zorunda değildir; yani, özel bir tür yalnızca `norm(A)`'yi ikinci argüman olmadan uygulayabilir.

Bir matrisin operatör normunu hesaplamak için [`opnorm`](@ref) kullanın.

# Örnekler

```jldoctest
julia> v = [3, -2, 6]
3-element Vector{Int64}:
  3
 -2
  6

julia> norm(v)
7.0

julia> norm(v, 1)
11.0

julia> norm(v, Inf)
6.0

julia> norm([1 2 3; 4 5 6; 7 8 9])
16.881943016134134

julia> norm([1 2 3 4 5 6 7 8 9])
16.881943016134134

julia> norm(1:9)
16.881943016134134

julia> norm(hcat(v,v), 1) == norm(vcat(v,v), 1) != norm([v,v], 1)
true

julia> norm(hcat(v,v), 2) == norm(vcat(v,v), 2) == norm([v,v], 2)
true

julia> norm(hcat(v,v), Inf) == norm(vcat(v,v), Inf) != norm([v,v], Inf)
true
```
