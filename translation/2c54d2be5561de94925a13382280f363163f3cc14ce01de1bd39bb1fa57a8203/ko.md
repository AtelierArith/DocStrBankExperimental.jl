```
show([io::IO = stdout], x)
```

값 `x`의 텍스트 표현을 출력 스트림 `io`에 씁니다. 새로운 타입 `T`는 `show(io::IO, x::T)`를 오버로드해야 합니다. `show`에서 사용되는 표현은 일반적으로 줄리아 고유의 형식 및 타입 정보를 포함하며, 가능한 경우 파싱 가능한 줄리아 코드여야 합니다.

[`repr`](@ref)는 `show`의 출력을 문자열로 반환합니다.

타입 `T`의 객체에 대해 보다 자세한 사람이 읽을 수 있는 텍스트 출력을 원한다면, 추가로 `show(io::IO, ::MIME"text/plain", ::T)`를 정의하십시오. 이러한 메서드에서 `io`의 `:compact` [`IOContext`](@ref) 키(종종 `get(io, :compact, false)::Bool`로 확인됨)를 확인하는 것이 좋습니다. 일부 컨테이너는 `:compact => true`로 이 메서드를 호출하여 요소를 표시합니다.

또한 장식이 없는 표현을 작성하는 [`print`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> show("Hello World!")
"Hello World!"
julia> print("Hello World!")
Hello World!
```
