```
readdlm(source, delim::AbstractChar, T::Type, eol::AbstractChar; header=false, skipstart=0, skipblanks=true, use_mmap, quotes=true, dims, comments=false, comment_char='#')
```

소스에서 행렬을 읽어옵니다. 각 행은 `eol`로 구분되며, 요소는 주어진 구분자로 구분됩니다. 소스는 텍스트 파일, 스트림 또는 바이트 배열일 수 있습니다. 메모리 맵 파일은 매핑된 세그먼트의 바이트 배열 표현을 소스로 전달하여 사용할 수 있습니다.

`T`가 숫자 유형인 경우, 결과는 해당 유형의 배열이며, 비숫자 요소는 부동 소수점 유형의 경우 `NaN` 또는 0으로 처리됩니다. `T`의 다른 유용한 값으로는 `String`, `AbstractString`, 및 `Any`가 있습니다.

`header`가 `true`인 경우, 데이터의 첫 번째 행이 헤더로 읽히며, `(data_cells, header_cells)` 튜플이 반환됩니다.

`skipstart`를 지정하면 입력의 해당 수의 초기 행이 무시됩니다.

`skipblanks`가 `true`인 경우, 입력의 빈 행이 무시됩니다.

`use_mmap`가 `true`인 경우, `source`로 지정된 파일이 메모리 맵으로 되어 있어 파일이 클 경우 속도가 향상될 수 있습니다. 기본값은 `false`입니다. Windows 파일 시스템에서는 파일이 한 번만 읽히고 쓰이지 않는 경우가 아니면 `use_mmap`를 `true`로 설정해서는 안 됩니다. OS가 유닉스 계열이지만 파일 시스템이 윈도우 계열인 엣지 케이스가 존재합니다.

`quotes`가 `true`인 경우, 큰따옴표(")로 둘러싸인 열은 새 줄 및 열 구분자를 포함할 수 있습니다. 인용된 필드 내의 큰따옴표 문자는 다른 큰따옴표로 이스케이프해야 합니다. 예상되는 행과 열의 튜플로 `dims`를 지정하면 대용량 파일 읽기가 빨라질 수 있습니다. `comments`가 `true`인 경우, `comment_char`로 시작하는 행과 해당 행의 `comment_char` 뒤의 텍스트는 무시됩니다.

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
