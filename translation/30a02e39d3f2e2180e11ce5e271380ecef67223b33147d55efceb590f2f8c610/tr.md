```
a ? b : c
```

Kısa formda koşullu ifadeler; "eğer `a` doğruysa, `b`'yi değerlendir, aksi takdirde `c`'yi değerlendir" şeklinde okunur. Ayrıca [ternary operator](https://en.wikipedia.org/wiki/%3F:) olarak da bilinir.

Bu sözdizimi `if a; b else c end` ile eşdeğerdir, ancak genellikle `b` veya `c` değerinin daha büyük bir ifadenin parçası olarak kullanıldığını vurgulamak için kullanılır, `b` veya `c`'yi değerlendirmenin yan etkilerinden ziyade.

Daha fazla ayrıntı için [kontrol akışı](@ref man-conditional-evaluation) bölümüne bakın.

# Örnekler

```jldoctest
julia> x = 1; y = 2;

julia> x > y ? println("x daha büyük") : println("x daha büyük değil")
x daha büyük değil

julia> x > y ? "x daha büyük" : x == y ? "x ve y eşit" : "y daha büyük"
"y daha büyük"
```
