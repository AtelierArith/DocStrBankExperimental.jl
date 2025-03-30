```
writedlm(f, A, delim='\t'; opts)
```

`A`'yı (bir vektör, matris veya yinelemeli satırlardan oluşan bir koleksiyon) verilen ayırıcı `delim` (varsayılan olarak sekme, ancak herhangi bir yazdırılabilir Julia nesnesi, genellikle bir `Char` veya `AbstractString` olabilir) kullanarak `f`'ye (ya bir dosya adı dizesi ya da bir `IO` akışı) metin olarak yazın.

Örneğin, aynı uzunlukta iki vektör `x` ve `y`, `writedlm(f, [x y])` veya `writedlm(f, zip(x, y))` ile `f`'ye sekme ile ayrılmış metin olarak iki sütun olarak yazılabilir.

# Örnekler

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
