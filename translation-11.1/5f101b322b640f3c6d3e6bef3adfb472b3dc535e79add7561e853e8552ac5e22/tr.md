```
eachline(io::IO=stdin; keep::Bool=false)
eachline(filename::AbstractString; keep::Bool=false)
```

Bir I/O akışı veya dosyadan her satırı verecek bir iterable `EachLine` nesnesi oluşturur. İterasyon, `keep` parametresi ile birlikte akış argümanında [`readline`](@ref) çağrıları yaparak, sonundaki satır sonu karakterlerinin korunup korunmayacağını belirler. Bir dosya adı ile çağrıldığında, dosya iterasyonun başında bir kez açılır ve sonunda kapatılır. İterasyon kesilirse, dosya `EachLine` nesnesi çöp toplandığında kapatılacaktır.

Bir `String`'in her satırını yinelemek için `eachline(IOBuffer(str))` kullanılabilir.

[`Iterators.reverse`](@ref) bir `EachLine` nesnesinde ters sırayla satırları okumak için kullanılabilir (dosyalar, tamponlar ve [`seek`](@ref) destekleyen diğer I/O akışları için) ve [`first`](@ref) veya [`last`](@ref) başlangıç veya son satırları çıkarmak için kullanılabilir.

# Örnekler

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for line in eachline("my_file.txt")
           print(line)
       end
JuliaLang is a GitHub organization. It has many members.

julia> rm("my_file.txt");
```

!!! compat "Julia 1.8"
    `Iterators.reverse` veya `last` ile `eachline` iteratörlerini kullanmak için Julia 1.8 gereklidir.

