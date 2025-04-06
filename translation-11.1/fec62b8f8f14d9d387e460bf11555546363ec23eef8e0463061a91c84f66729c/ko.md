```
where
```

`where` 키워드는 [`UnionAll`](@ref) 타입을 생성하며, 이는 어떤 변수의 모든 값에 대해 다른 타입의 반복된 합집합으로 생각할 수 있습니다. 예를 들어 `Vector{T} where T<:Real`은 요소 타입이 어떤 종류의 `Real` 숫자인 모든 [`Vector`](@ref)를 포함합니다.

변수 바인드는 생략할 경우 기본적으로 [`Any`](@ref)로 설정됩니다:

```julia
Vector{T} where T    # `where T<:Any`의 약어
```

변수는 하한을 가질 수도 있습니다:

```julia
Vector{T} where T>:Int
Vector{T} where Int<:T<:Real
```

중첩된 `where` 표현식에 대한 간결한 구문도 있습니다. 예를 들어, 다음과 같은 표현식:

```julia
Pair{T, S} where S<:Array{T} where T<:Number
```

는 다음과 같이 줄일 수 있습니다:

```julia
Pair{T, S} where {T<:Number, S<:Array{T}}
```

이 형태는 메서드 시그니처에서 자주 발견됩니다.

이 형태에서는 변수가 바깥쪽부터 나열된다는 점에 유의하세요. 이는 타입이 `T{p1, p2, ...}` 구문을 사용하여 매개변수 값에 "적용"될 때 변수들이 치환되는 순서와 일치합니다.
