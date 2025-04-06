```
DateTime(dt::AbstractString, format::AbstractString; locale="english") -> DateTime
```

`dt` 날짜 시간 문자열을 `format` 문자열에 주어진 패턴에 따라 파싱하여 `DateTime`을 생성합니다 (구문에 대한 내용은 [`DateFormat`](@ref)를 참조하십시오).

!!! note
    이 메서드는 호출될 때마다 `DateFormat` 객체를 생성합니다. 동일한 형식을 반복해서 사용할 때 성능 저하를 피하기 위해 대신 [`DateFormat`](@ref) 객체를 생성하고 이를 두 번째 인수로 사용하는 것이 좋습니다.


# 예제

```jldoctest
julia> DateTime("2020-01-01", "yyyy-mm-dd")
2020-01-01T00:00:00

julia> a = ("2020-01-01", "2020-01-02");

julia> [DateTime(d, dateformat"yyyy-mm-dd") for d ∈ a] # 선호됨
2-element Vector{DateTime}:
 2020-01-01T00:00:00
 2020-01-02T00:00:00
```
