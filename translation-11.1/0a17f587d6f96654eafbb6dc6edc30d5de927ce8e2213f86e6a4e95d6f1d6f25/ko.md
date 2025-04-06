```
@fastmath expr
```

변환된 표현식을 실행합니다. 이 표현식은 엄격한 IEEE 의미를 위반할 수 있는 함수를 호출합니다. 이는 가능한 가장 빠른 연산을 허용하지만 결과는 정의되지 않으므로 주의해야 합니다. 이렇게 하면 수치 결과가 변경될 수 있습니다.

이것은 [LLVM Fast-Math 플래그](https://llvm.org/docs/LangRef.html#fast-math-flags)를 설정하며, clang의 `-ffast-math` 옵션에 해당합니다. 자세한 내용은 [성능 주석에 대한 노트](@ref man-performance-annotations)를 참조하십시오.

# 예제

```jldoctest
julia> @fastmath 1+2
3

julia> @fastmath(sin(3))
0.1411200080598672
```
