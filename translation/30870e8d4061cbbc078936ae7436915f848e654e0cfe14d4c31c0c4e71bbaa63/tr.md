```
|>(x, f)
```

Fonksiyonu `f` argüman `x`'e uygulayan infiks operatör. Bu, `f(g(x))` ifadesinin `x |> g |> f` şeklinde yazılmasına olanak tanır. Anonim fonksiyonlarla kullanıldığında, istenen zinciri elde etmek için tanımın etrafında parantezlerin genellikle gerekli olduğu durumlar vardır.

# Örnekler

```jldoctest
julia> 4 |> inv
0.25

julia> [2, 3, 5] |> sum |> inv
0.1

julia> [0 1; 2 3] .|> (x -> x^2) |> sum
14
```
