```
string(xs...)
```

Herhangi bir değerden bir dize oluşturmak için [`print`](@ref) işlevini kullanın.

`string` genellikle doğrudan tanımlanmamalıdır. Bunun yerine, `print(io::IO, x::MyType)` yöntemini tanımlayın. Belirli bir tür için `string(x)` yüksek verimli olması gerekiyorsa, `string`'e bir yöntem eklemek ve `print(io::IO, x::MyType) = print(io, string(x))` tanımlamak mantıklı olabilir; bu, işlevlerin tutarlı olmasını sağlar.

Ayrıca bakınız: [`String`](@ref), [`repr`](@ref), [`sprint`](@ref), [`show`](@ref @show).

# Örnekler

```jldoctest
julia> string("a", 1, true)
"a1true"
```
