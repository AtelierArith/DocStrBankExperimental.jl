```
Profile.Allocs.@profile [sample_rate=0.1] expr
```

`expr` 동안 발생하는 프로파일 할당을 프로파일링하며, 결과와 AllocResults 구조체를 모두 반환합니다.

샘플 비율이 1.0이면 모든 것을 기록하고; 0.0이면 아무것도 기록하지 않습니다.

```julia
julia> Profile.Allocs.@profile sample_rate=0.01 peakflops()
1.03733270279065e11

julia> results = Profile.Allocs.fetch()

julia> last(sort(results.allocs, by=x->x.size))
Profile.Allocs.Alloc(Vector{Any}, Base.StackTraces.StackFrame[_new_array_ at array.c:127, ...], 5576)
```

자세한 정보는 Julia 문서의 프로파일링 튜토리얼을 참조하세요.

!!! compat "Julia 1.11"
    이전 버전의 Julia는 모든 경우에 타입을 캡처할 수 없었습니다. 이전 버전의 Julia에서 `Profile.Allocs.UnknownType` 타입의 할당을 보게 되면, 이는 프로파일러가 할당된 객체의 타입을 알지 못한다는 의미입니다. 이는 주로 컴파일러에 의해 생성된 코드에서 할당이 발생할 때 발생했습니다. 자세한 내용은 [issue #43688](https://github.com/JuliaLang/julia/issues/43688)를 참조하세요.

    Julia 1.11부터는 모든 할당에 대해 보고된 타입이 있어야 합니다.


!!! compat "Julia 1.8"
    할당 프로파일러는 Julia 1.8에 추가되었습니다.

