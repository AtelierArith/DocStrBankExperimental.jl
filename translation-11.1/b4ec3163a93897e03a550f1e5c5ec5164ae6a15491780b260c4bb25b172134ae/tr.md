```
broadcast(f, As...)
```

Fonksiyonu `f` diziler, demetler, koleksiyonlar, [`Ref`](@ref)s ve/veya skalarlar `As` üzerinde yayar.

Yayılma, fonksiyonu `f` konteyner argümanlarının elemanları ve `As` içindeki skalarlar üzerinde uygular. Tekil ve eksik boyutlar, diğer argümanların boyutlarıyla eşleşecek şekilde sanal olarak değeri tekrar ederek genişletilir. Varsayılan olarak, yalnızca sınırlı sayıda tür skalar olarak kabul edilir; bunlar arasında `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s ve [`missing`](@ref) ve [`nothing`](@ref) gibi bazı yaygın tekil değerler bulunur. Diğer tüm argümanlar eleman bazında yinelemeli veya dizinlenir.

Sonuçta oluşan konteyner türü aşağıdaki kurallara göre belirlenir:

  * Tüm argümanlar skalar veya sıfır boyutlu diziler ise, bir sarılmamış skalar döner.
  * En az bir argüman bir demet ise ve diğerleri skalar veya sıfır boyutlu diziler ise, bir demet döner.
  * Diğer tüm argüman kombinasyonları varsayılan olarak bir `Array` döner, ancak özel konteyner türleri, argüman olarak göründüklerinde sonucu özelleştirmek için kendi uygulamalarını ve terfi benzeri kurallarını tanımlayabilir.

Yayılma için özel bir sözdizimi vardır: `f.(args...)` ifadesi `broadcast(f, args...)` ile eşdeğerdir ve iç içe `f.(g.(args...))` çağrıları tek bir yayılma döngüsünde birleştirilir.

# Örnekler

```jldoctest
julia> A = [1, 2, 3, 4, 5]
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> B = [1 2; 3 4; 5 6; 7 8; 9 10]
5×2 Matrix{Int64}:
 1   2
 3   4
 5   6
 7   8
 9  10

julia> broadcast(+, A, B)
5×2 Matrix{Int64}:
  2   3
  5   6
  8   9
 11  12
 14  15

julia> parse.(Int, ["1", "2"])
2-element Vector{Int64}:
 1
 2

julia> abs.((1, -2))
(1, 2)

julia> broadcast(+, 1.0, (0, -2.0))
(1.0, -1.0)

julia> (+).([[0,2], [1,3]], Ref{Vector{Int}}([1,-1]))
2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]

julia> string.(("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"

```
