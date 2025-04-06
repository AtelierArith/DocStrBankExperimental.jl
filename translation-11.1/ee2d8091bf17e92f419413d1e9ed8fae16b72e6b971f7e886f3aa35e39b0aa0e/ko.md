# SIMD Support

`VecElement{T}` 타입은 SIMD 연산 라이브러리를 구축하기 위해 설계되었습니다. 이를 실제로 사용하려면 `llvmcall`을 사용해야 합니다. 이 타입은 다음과 같이 정의됩니다:

```julia
struct VecElement{T}
    value::T
end
```

특별한 컴파일 규칙이 있습니다: 동질적인 튜플 `VecElement{T}`는 `T`가 원시 비트 타입일 때 LLVM `vector` 타입으로 매핑됩니다.

`-O3`에서 컴파일러는 이러한 튜플에 대한 연산을 자동으로 벡터화할 *수 있습니다*. 예를 들어, 다음 프로그램은 `julia -O3`로 컴파일할 때 x86 시스템에서 두 개의 SIMD 덧셈 명령어(`addps`)를 생성합니다:

```julia
const m128 = NTuple{4,VecElement{Float32}}

function add(a::m128, b::m128)
    (VecElement(a[1].value+b[1].value),
     VecElement(a[2].value+b[2].value),
     VecElement(a[3].value+b[3].value),
     VecElement(a[4].value+b[4].value))
end

triple(c::m128) = add(add(c,c),c)

code_native(triple,(m128,))
```

그러나 자동 벡터화에 의존할 수 없기 때문에, 향후 사용은 주로 `llvmcall`을 사용하는 라이브러리를 통해 이루어질 것입니다.
