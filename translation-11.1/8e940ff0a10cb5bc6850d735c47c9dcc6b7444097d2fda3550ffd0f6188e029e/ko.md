```
@inbounds(blk)
```

표현식 내에서 배열 경계 검사를 제거합니다.

아래 예제에서는 배열 `A`의 요소 `i`를 참조하기 위한 범위 내 검사가 생략되어 성능이 향상됩니다.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

!!! 경고     `@inbounds`를 사용하면 경계 밖의 인덱스에 대해 잘못된 결과/충돌/손상이 발생할 수 있습니다. 사용자는 이를 수동으로 확인할 책임이 있습니다. 모든 접근이 경계 내에 있다는 것이 지역적으로 사용 가능한 정보로부터 확실할 때만 `@inbounds`를 사용하십시오. 특히, 위와 같은 함수에서 `eachindex(A)` 대신 `1:length(A)`를 사용하는 것은 *안전하게 경계 내에 있지 않습니다* 왜냐하면 `A`의 첫 번째 인덱스가 `AbstractArray`를 서브타입으로 하는 모든 사용자 정의 유형에 대해 항상 `1`이 아닐 수 있기 때문입니다.
