```
^(x, y)
```

지수 연산자.

`x`와 `y`가 정수인 경우 결과가 오버플로우될 수 있습니다. 과학적 표기법으로 숫자를 입력하려면 `1.2 * 10^3` 대신 [`Float64`](@ref) 리터럴인 `1.2e3`을 사용하세요.

`y`가 `Int` 리터럴(예: `x^2`의 `2` 또는 `x^-3`의 `-3`)인 경우, Julia 코드는 컴파일러에 의해 `Base.literal_pow(^, x, Val(y))`로 변환되어 지수의 값에 대한 컴파일 타임 특수화를 가능하게 합니다. (기본적으로 우리는 `Base.literal_pow(^, x, Val(y)) = ^(x,y)`를 가지고 있으며, 일반적으로 `^ == Base.^`입니다. 단, `^`가 호출 네임스페이스에서 정의되지 않은 경우에 한합니다.) `y`가 음의 정수 리터럴인 경우, 기본적으로 `Base.literal_pow`는 연산을 `inv(x)^-y`로 변환하며, 여기서 `-y`는 양수입니다.

또한 [`exp2`](@ref), [`<<`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> 3^5
243

julia> 3^-1  # Base.literal_pow 사용
0.3333333333333333

julia> p = -1;

julia> 3^p
ERROR: DomainError with -1:
Cannot raise an integer x to a negative power -1.
[...]

julia> 3.0^p
0.3333333333333333

julia> 10^19 > 0  # 정수 오버플로우
false

julia> big(10)^19 == 1e19
true
```
