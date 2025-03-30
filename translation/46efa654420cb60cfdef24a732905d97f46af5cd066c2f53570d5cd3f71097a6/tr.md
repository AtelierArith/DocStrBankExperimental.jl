```
splat(f)
```

Eşdeğer

```julia
    my_splat(f) = args->f(args...)
```

yani, bir fonksiyon verildiğinde, orijinal fonksiyona bir argüman alıp onu yayarak yeni bir fonksiyon döndürür. Bu, çok argümanlı bir fonksiyonu tek bir argüman bekleyen bir bağlamda geçirebilmek için bir adaptör olarak kullanışlıdır, ancak o tek argüman olarak bir demet geçirir.

# Örnekler

```jldoctest
julia> map(splat(+), zip(1:3,4:6))
3-element Vector{Int64}:
 5
 7
 9

julia> my_add = splat(+)
splat(+)

julia> my_add((1,2,3))
6
```
