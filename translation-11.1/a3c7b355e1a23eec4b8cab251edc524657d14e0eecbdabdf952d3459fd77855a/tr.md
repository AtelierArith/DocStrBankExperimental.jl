```
joinpath(parts::AbstractString...) -> String
joinpath(parts::Vector{AbstractString}) -> String
joinpath(parts::Tuple{AbstractString}) -> String
```

Yol bileşenlerini tam bir yola birleştirir. Eğer bazı argümanlar mutlak bir yol ise veya (Windows'ta) önceki yolların birleştirilmesi için hesaplanan sürücü ile eşleşmeyen bir sürücü belirtimi varsa, o zaman önceki bileşenler atılır.

Windows'ta her sürücü için bir geçerli dizin bulunduğundan, `joinpath("c:", "foo")` "c:" sürücüsündeki geçerli dizine göre bir yol temsil eder, bu nedenle bu "c:foo" ile eşdeğerdir, "c:\foo" ile değil. Dahası, `joinpath` bunu mutlak bir yol olarak kabul etmez ve sürücü harfi büyük/küçük harf duyarlılığını göz ardı eder, bu nedenle `joinpath("C:\A","c:b") = "C:\A\b"`.

# Örnekler

```jldoctest
julia> joinpath("/home/myuser", "example.jl")
"/home/myuser/example.jl"
```

```jldoctest
julia> joinpath(["/home/myuser", "example.jl"])
"/home/myuser/example.jl"
```
