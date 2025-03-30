```
islowercase(c::AbstractChar) -> Bool
```

문자가 소문자(letter)인지 테스트합니다 (유니코드 표준의 `Lowercase` 파생 속성에 따라).

또한 [`isuppercase`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> islowercase('α')
true

julia> islowercase('Γ')
false

julia> islowercase('❤')
false
```
