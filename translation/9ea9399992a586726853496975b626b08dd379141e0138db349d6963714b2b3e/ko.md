```
writedlm(f, A, delim='\t'; opts)
```

`A` (벡터, 행렬 또는 반복 가능한 행의 반복 가능한 컬렉션)을 주어진 구분 기호 `delim` (기본값은 탭이지만, 일반적으로 `Char` 또는 `AbstractString`인 인쇄 가능한 Julia 객체일 수 있음)을 사용하여 `f` (파일 이름 문자열 또는 `IO` 스트림)로 텍스트로 작성합니다.

예를 들어, 길이가 같은 두 벡터 `x`와 `y`는 `writedlm(f, [x y])` 또는 `writedlm(f, zip(x, y))`를 사용하여 `f`에 탭으로 구분된 텍스트의 두 열로 작성할 수 있습니다.

# 예제

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
