```
Time(t::AbstractString, format::AbstractString; locale="english") -> Time
```

`format` 문자열에 따라 `t` 시간 문자열을 파싱하여 `Time`을 생성합니다 (구문에 대한 자세한 내용은 [`DateFormat`](@ref)를 참조하십시오).

!!! note
    이 메서드는 호출될 때마다 `DateFormat` 객체를 생성합니다. 동일한 형식을 반복해서 사용할 때 성능 저하를 피하기 위해 대신 [`DateFormat`](@ref) 객체를 생성하고 이를 두 번째 인수로 사용하는 것이 좋습니다.


# 예제

```jldoctest
julia> Time("12:34pm", "HH:MMp")
12:34:00

julia> a = ("12:34pm", "2:34am");

julia> [Time(d, dateformat"HH:MMp") for d ∈ a] # 선호됨
2-element Vector{Time}:
 12:34:00
 02:34:00
```
