```
dot(x, y)
x ⋅ y
```

İki vektör arasındaki nokta çarpımını hesaplayın. Karmaşık vektörler için, ilk vektör konjuge edilir.

`dot` ayrıca, `dot`'un elemanlar üzerinde tanımlı olduğu sürece, herhangi bir boyuttaki diziler de dahil olmak üzere, rastgele yinelemeli nesnelerde de çalışır.

`dot`, argümanların eşit uzunlukta olması kısıtlaması ile birlikte, `sum(dot(vx,vy) for (vx,vy) in zip(x, y))` ile anlamsal olarak eşdeğerdir.

`x ⋅ y` (burada `⋅`, REPL'de `\cdot` yazarak tamamlanabilir) `dot(x, y)` için bir eşanlamlıdır.

# Örnekler

```jldoctest
julia> dot([1; 1], [2; 3])
5

julia> dot([im; im], [1; 1])
0 - 2im

julia> dot(1:5, 2:6)
70

julia> x = fill(2., (5,5));

julia> y = fill(3., (5,5));

julia> dot(x, y)
150.0
```
