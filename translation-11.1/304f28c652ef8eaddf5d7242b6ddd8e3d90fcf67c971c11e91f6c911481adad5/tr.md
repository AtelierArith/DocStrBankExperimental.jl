```
@sprintf("%Fmt", args...)
```

Dize [`@printf`](@ref) biçimlendirilmiş çıktıyı dize olarak döndürür.

# Örnekler

```jldoctest
julia> @sprintf "this is a %s %15.1f" "test" 34.567
"this is a test            34.6"
```
