`Broadcast.AbstractArrayStyle{N} <: BroadcastStyle`는 `AbstractArray` 유형과 관련된 모든 스타일의 추상 슈퍼타입입니다. `N` 매개변수는 차원 수를 나타내며, 특정 차원 수만 지원하는 AbstractArray 유형에 유용할 수 있습니다:

```
struct SparseMatrixStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatrixStyle()
```

임의의 차원 수를 지원하는 `AbstractArray` 유형의 경우, `N`을 `Any`로 설정할 수 있습니다:

```
struct MyArrayStyle <: Broadcast.AbstractArrayStyle{Any} end
Base.BroadcastStyle(::Type{<:MyArray}) = MyArrayStyle()
```

여러 `AbstractArrayStyle`을 혼합하고 차원 수를 추적할 수 있도록 하려면, 스타일이 [`Val`](@ref) 생성자를 지원해야 합니다:

```
struct MyArrayStyleDim{N} <: Broadcast.AbstractArrayStyle{N} end
(::Type{<:MyArrayStyleDim})(::Val{N}) where N = MyArrayStyleDim{N}()
```

두 개 이상의 `AbstractArrayStyle` 서브타입이 충돌하는 경우, 브로드캐스팅 기계는 `Array`를 생성하는 것으로 되돌아갑니다. 이것이 바람직하지 않은 경우, 출력 유형을 제어하기 위해 이진 [`BroadcastStyle`](@ref) 규칙을 정의해야 할 수 있습니다.

또한 [`Broadcast.DefaultArrayStyle`](@ref)를 참조하십시오.
