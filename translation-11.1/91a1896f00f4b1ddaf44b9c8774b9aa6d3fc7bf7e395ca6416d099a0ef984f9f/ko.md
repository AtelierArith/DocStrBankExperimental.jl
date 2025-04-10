```
@views 표현식
```

주어진 표현식(이는 `begin`/`end` 블록, 루프, 함수 등일 수 있음)에서 모든 배열 슬라이싱 작업을 뷰를 반환하도록 변환합니다. 스칼라 인덱스, 비배열 유형 및 명시적 [`getindex`](@ref) 호출(즉, `array[...]`가 아닌)은 영향을 받지 않습니다.

유사하게, `@views`는 문자열 슬라이스를 [`SubString`](@ref) 뷰로 변환합니다.

!!! 주의     `@views` 매크로는 주어진 `expression`에 명시적으로 나타나는 `array[...]` 표현식에만 영향을 미치며, 해당 코드에 의해 호출되는 함수에서 발생하는 배열 슬라이싱에는 영향을 미치지 않습니다.

!!! 호환성 "Julia 1.5"     인덱싱 표현식에서 첫 번째 인덱스를 참조하기 위해 `begin`을 사용하는 것은 Julia 1.4에서 구현되었지만, Julia 1.5부터 `@views`에 의해 지원되었습니다.

# 예시

```jldoctest
julia> A = zeros(3, 3);

julia> @views for row in 1:3
           b = A[row, :] # b는 복사가 아닌 뷰입니다
           b .= row      # 모든 요소를 행 인덱스로 할당
       end

julia> A
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 2.0  2.0  2.0
 3.0  3.0  3.0
```
