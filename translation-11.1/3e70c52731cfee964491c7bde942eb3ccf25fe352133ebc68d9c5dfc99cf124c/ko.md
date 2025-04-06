```
 isidentifier(s) -> Bool
```

문자열 `s`가 Julia 코드에서 유효한 일반 식별자로 구문 분석되는 문자를 포함하는지 여부를 반환합니다(이진/단항 연산자가 아님); [`Base.isoperator`](@ref)도 참조하십시오.

내부적으로 Julia는 `Symbol`에서 모든 문자 시퀀스를 허용합니다(단, `\0` 제외) 및 매크로는 주변 코드와의 이름 충돌을 피하기 위해 `#`가 포함된 변수 이름을 자동으로 사용합니다. 파서가 변수를 인식하기 위해서는 제한된 문자 집합을 사용합니다(유니코드에 의해 크게 확장됨). `isidentifier()`는 기호가 유효한 문자를 포함하는지 여부를 파서에 직접 쿼리할 수 있게 해줍니다.

# 예제

```jldoctest
julia> Meta.isidentifier(:x), Meta.isidentifier("1x")
(true, false)
```
