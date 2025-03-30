```
readdlm(source, delim::AbstractChar; options...)
```

행 끝 구분자는 `\n`으로 간주됩니다. 모든 데이터가 숫자인 경우 결과는 숫자 배열이 됩니다. 일부 요소를 숫자로 구문 분석할 수 없는 경우 숫자와 문자열의 이질적인 배열이 반환됩니다.

# 예제

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [1.1; 2.2; 3.3; 4.4];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y], ',')
       end;

julia> readdlm("delim_file.txt", ',')
4×2 Matrix{Float64}:
 1.0  1.1
 2.0  2.2
 3.0  3.3
 4.0  4.4

julia> z = ["a"; "b"; "c"; "d"];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x z], ',')
       end;

julia> readdlm("delim_file.txt", ',')
4×2 Matrix{Any}:
 1  "a"
 2  "b"
 3  "c"
 4  "d"

julia> rm("delim_file.txt")
```
