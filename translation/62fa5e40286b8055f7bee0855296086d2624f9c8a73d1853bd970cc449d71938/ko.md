```
replace([io::IO], s::AbstractString, pat=>r, [pat2=>r2, ...]; [count::Integer])
```

주어진 패턴 `pat`을 `s`에서 검색하고 각 발생을 `r`로 교체합니다. `count`가 제공되면 최대 `count` 개의 발생만 교체합니다. `pat`은 단일 문자, 벡터 또는 문자 집합, 문자열 또는 정규 표현식일 수 있습니다. 만약 `r`이 함수라면, 각 발생은 `r(s)`로 교체되며 여기서 `s`는 일치하는 하위 문자열(이때 `pat`이 `AbstractPattern` 또는 `AbstractString`인 경우) 또는 문자(이때 `pat`이 `AbstractChar` 또는 `AbstractChar`의 모음인 경우)입니다. 만약 `pat`이 정규 표현식이고 `r`이 [`SubstitutionString`](@ref)이라면, `r`의 캡처 그룹 참조는 해당 일치하는 텍스트로 교체됩니다. `string`에서 `pat`의 인스턴스를 제거하려면 `r`을 빈 `String`(`""`)으로 설정합니다.

반환 값은 교체 후의 새로운 문자열입니다. `io::IO` 인수가 제공되면 변환된 문자열이 대신 `io`에 기록됩니다(즉, `io`를 반환). (예를 들어, 이는 [`IOBuffer`](@ref)와 함께 사용되어 미리 할당된 버퍼 배열을 제자리에서 재사용하는 데 사용할 수 있습니다.)

여러 패턴을 지정할 수 있으며, 이들은 왼쪽에서 오른쪽으로 동시에 적용되므로, 어떤 문자에도 하나의 패턴만 적용되며, 패턴은 입력 텍스트에만 적용되고 교체에는 적용되지 않습니다.

!!! compat "Julia 1.7"
    여러 패턴에 대한 지원은 1.7 버전을 요구합니다.


!!! compat "Julia 1.10"
    `io::IO` 인수는 1.10 버전을 요구합니다.


# 예제

```jldoctest
julia> replace("Python is a programming language.", "Python" => "Julia")
"Julia is a programming language."

julia> replace("The quick foxes run quickly.", "quick" => "slow", count=1)
"The slow foxes run quickly."

julia> replace("The quick foxes run quickly.", "quick" => "", count=1)
"The  foxes run quickly."

julia> replace("The quick foxes run quickly.", r"fox(es)?" => s"bus\1")
"The quick buses run quickly."

julia> replace("abcabc", "a" => "b", "b" => "c", r".+" => "a")
"bca"
```
