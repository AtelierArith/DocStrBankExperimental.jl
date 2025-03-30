```
length(s::AbstractString) -> Int
length(s::AbstractString, i::Integer, j::Integer) -> Int
```

문자열 `s`의 인덱스 `i`에서 `j`까지의 문자 수를 반환합니다.

이는 `i`에서 `j`까지의 유효한 문자 인덱스인 코드 유닛 인덱스의 수로 계산됩니다. 단일 문자열 인수만 있는 경우, 전체 문자열의 문자 수를 계산합니다. `i`와 `j` 인수가 있는 경우, 문자열 `s`에서 유효한 인덱스인 `i`와 `j` 사이의 인덱스 수를 계산합니다. 범위 내 값 외에도, `i`는 범위를 벗어난 값 `ncodeunits(s) + 1`을 가질 수 있으며, `j`는 범위를 벗어난 값 `0`을 가질 수 있습니다.

!!! note
    이 작업의 시간 복잡도는 일반적으로 선형입니다. 즉, 문자열의 바이트 또는 문자 수에 비례하는 시간이 소요됩니다. 이는 값을 즉시 계산하기 때문입니다. 이는 배열에 대한 메서드와는 대조적이며, 배열에 대한 메서드는 상수 시간 작업입니다.


또한 [`isvalid`](@ref), [`ncodeunits`](@ref), [`lastindex`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> length("jμΛIα")
5
```
