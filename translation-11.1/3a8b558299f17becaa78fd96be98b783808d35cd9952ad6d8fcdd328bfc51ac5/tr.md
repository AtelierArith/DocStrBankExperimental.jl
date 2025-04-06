```
A::AbstractArray'ı tekrar ederek bir dizi oluşturun. inner'ın i'inci elemanı, A'nın i'inci boyutunun bireysel girişlerinin kaç kez tekrar edileceğini belirtir. outer'ın i'inci elemanı, A'nın i'inci boyutu boyunca bir dilimin kaç kez tekrar edileceğini belirtir. inner veya outer atlandığında, tekrar yapılmaz.

# Örnekler

```

jldoctest julia> repeat(1:2, inner=2) 4-element Vector{Int64}:  1  1  2  2

julia> repeat(1:2, outer=2) 4-element Vector{Int64}:  1  2  1  2

julia> repeat([1 2; 3 4], inner=(2, 1), outer=(1, 3)) 4×6 Matrix{Int64}:  1  2  1  2  1  2  1  2  1  2  1  2  3  4  3  4  3  4  3  4  3  4  3  4

```

```
