```
...
```

"Splat" operatörü, `...`, bir dizi argümanı temsil eder. `...`, bir işlev tanımında kullanılabilir; bu, işlevin rastgele sayıda argüman kabul ettiğini belirtir. `...`, bir işlevi bir dizi argümana uygulamak için de kullanılabilir.

# Örnekler

```jldoctest
julia> add(xs...) = reduce(+, xs)
add (generic function with 1 method)

julia> add(1, 2, 3, 4, 5)
15

julia> add([1, 2, 3]...)
6

julia> add(7, 1:100..., 1000:1100...)
111107
```
