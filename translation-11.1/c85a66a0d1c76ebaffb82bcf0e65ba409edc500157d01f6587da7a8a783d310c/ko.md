```
showable(mime, x)
```

주어진 `mime` 유형으로 객체 `x`를 쓸 수 있는지 여부를 나타내는 부울 값을 반환합니다.

(기본적으로, 이는 `typeof(x)`에 대한 해당 [`show`](@ref) 메서드의 존재에 의해 자동으로 결정됩니다. 일부 유형은 사용자 정의 `showable` 메서드를 제공합니다. 예를 들어, 사용 가능한 MIME 형식이 `x`의 *값*에 따라 달라질 수 있습니다.)

# 예시

```jldoctest
julia> showable(MIME("text/plain"), rand(5))
true

julia> showable("image/png", rand(5))
false
```
