```
eachline(io::IO=stdin; keep::Bool=false)
eachline(filename::AbstractString; keep::Bool=false)
```

I/O 스트림 또는 파일에서 각 줄을 생성하는 iterable `EachLine` 객체를 만듭니다. 반복 호출은 `keep`이 전달된 스트림 인수에서 [`readline`](@ref)를 반복적으로 호출하여 줄 끝의 개행 문자가 유지되는지 여부를 결정합니다. 파일 이름으로 호출되면, 반복의 시작 시 파일이 한 번 열리고 끝에서 닫힙니다. 반복이 중단되면, `EachLine` 객체가 가비지 컬렉션될 때 파일이 닫힙니다.

`String`의 각 줄을 반복하려면 `eachline(IOBuffer(str))`를 사용할 수 있습니다.

[`Iterators.reverse`](@ref)는 `EachLine` 객체에서 줄을 역순으로 읽는 데 사용할 수 있으며(파일, 버퍼 및 [`seek`](@ref)를 지원하는 기타 I/O 스트림에 대해), [`first`](@ref) 또는 [`last`](@ref)를 사용하여 각각 초기 또는 최종 줄을 추출할 수 있습니다.

# 예제

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for line in eachline("my_file.txt")
           print(line)
       end
JuliaLang is a GitHub organization. It has many members.

julia> rm("my_file.txt");
```

!!! compat "Julia 1.8"
    `eachline` 반복자와 함께 `Iterators.reverse` 또는 `last`를 사용하려면 Julia 1.8이 필요합니다.

