```
get(f::Union{Function, Type}, collection, key)
```

주어진 키에 대해 저장된 값을 반환하거나, 키에 대한 매핑이 없으면 `f()`를 반환합니다. 기본값을 사전에 저장하려면 [`get!`](@ref)를 사용하세요.

이것은 `do` 블록 구문을 사용하여 호출되도록 설계되었습니다.

```julia
get(dict, key) do
    # 기본값은 여기에서 계산됩니다.
    time()
end
```
