```
evalfile(path::AbstractString, args::Vector{String}=String[])
```

Dosyayı anonim bir modüle yükleyin, tüm ifadeleri değerlendirin ve son ifadenin değerini döndürün. İsteğe bağlı `args` argümanı, betiğin giriş argümanlarını ayarlamak için kullanılabilir (yani, küresel `ARGS` değişkeni). Tanımların (örneğin, yöntemler, küreseller) anonim modülde değerlendirildiğini ve mevcut modülü etkilemediğini unutmayın.

# Örnekler

```jldoctest
julia> write("testfile.jl", """
           @show ARGS
           1 + 1
       """);

julia> x = evalfile("testfile.jl", ["ARG1", "ARG2"]);
ARGS = ["ARG1", "ARG2"]

julia> x
2

julia> rm("testfile.jl")
```
