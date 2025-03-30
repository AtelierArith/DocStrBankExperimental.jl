```
isuppercase(c::AbstractChar) -> Bool
```

문자가 대문자(letter)인지 테스트합니다 (유니코드 표준의 `Uppercase` 파생 속성에 따라).

또한 [`islowercase`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> isuppercase('γ')
false

julia> isuppercase('Γ')
true

julia> isuppercase('❤')
false
```
