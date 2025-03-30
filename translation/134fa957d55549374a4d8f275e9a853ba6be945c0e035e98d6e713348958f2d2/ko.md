```
RegexMatch <: AbstractMatch
```

문자열에서 발견된 [`Regex`](@ref)에 대한 단일 일치를 나타내는 유형입니다. 일반적으로 [`match`](@ref) 함수에서 생성됩니다.

`match` 필드는 전체 일치하는 문자열의 부분 문자열을 저장합니다. `captures` 필드는 숫자로 인덱싱된 각 캡처 그룹의 부분 문자열을 저장합니다. 캡처 그룹 이름으로 인덱싱하려면 전체 일치 객체를 대신 인덱싱해야 하며, 예제에서 보여줍니다. 일치의 시작 위치는 `offset` 필드에 저장됩니다. `offsets` 필드는 각 캡처 그룹의 시작 위치를 저장하며, 0은 캡처되지 않은 그룹을 나타냅니다.

이 유형은 `Regex`의 캡처 그룹에 대한 반복자로 사용될 수 있으며, 각 그룹에서 캡처된 부분 문자열을 생성합니다. 이로 인해 일치의 캡처를 구조 분해할 수 있습니다. 그룹이 캡처되지 않은 경우 부분 문자열 대신 `nothing`이 생성됩니다.

`RegexMatch` 객체를 수용하는 메서드는 [`iterate`](@ref), [`length`](@ref), [`eltype`](@ref), [`keys`](@ref keys(::RegexMatch)), [`haskey`](@ref), 및 [`getindex`](@ref)에 대해 정의되어 있으며, 여기서 키는 캡처 그룹의 이름 또는 번호입니다. 더 많은 정보는 [`keys`](@ref keys(::RegexMatch))를 참조하십시오.

# 예제

```jldoctest
julia> m = match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30 in the morning")
RegexMatch("11:30", hour="11", minute="30", 3=nothing)

julia> m.match
"11:30"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "11"
 "30"
 nothing


julia> m["minute"]
"30"

julia> hr, min, ampm = m; # 캡처 그룹을 반복하여 구조 분해

julia> hr
"11"
```
