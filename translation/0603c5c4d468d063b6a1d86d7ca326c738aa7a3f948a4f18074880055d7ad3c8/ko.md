```
함수
```

함수는 `function` 키워드로 정의됩니다:

```julia
function add(a, b)
    return a + b
end
```

또는 짧은 형식 표기법:

```julia
add(a, b) = a + b
```

[`return`](@ref) 키워드의 사용은 다른 언어와 정확히 동일하지만, 종종 선택적입니다. 명시적인 `return` 문이 없는 함수는 함수 본문의 마지막 표현식을 반환합니다.
