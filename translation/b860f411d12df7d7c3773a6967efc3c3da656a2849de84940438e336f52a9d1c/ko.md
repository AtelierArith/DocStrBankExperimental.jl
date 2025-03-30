```
readdlm(source; options...)
```

열은 하나 이상의 공백으로 구분된 것으로 가정합니다. 줄 끝 구분자는 `\n`으로 간주됩니다. 모든 데이터가 숫자일 경우 결과는 숫자 배열이 됩니다. 일부 요소가 숫자로 구문 분석될 수 없는 경우 숫자와 문자열의 이질적인 배열이 반환됩니다.

# 예제

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = ["a"; "b"; "c"; "d"];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end;

julia> readdlm("delim_file.txt")
4×2 Matrix{Any}:
 1  "a"
 2  "b"
 3  "c"
 4  "d"

julia> rm("delim_file.txt")
```
