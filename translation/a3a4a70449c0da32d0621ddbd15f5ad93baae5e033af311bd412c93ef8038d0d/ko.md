```
angle(z)
```

복소수 `z`의 위상 각을 라디안 단위로 계산합니다.

`-pi ≤ angle(z) ≤ pi` 범위의 숫자를 반환하며, 따라서 음의 실축을 따라 불연속적입니다.

참고: [`atan`](@ref), [`cis`](@ref), [`rad2deg`](@ref).

# 예제

```jldoctest
julia> rad2deg(angle(1 + im))
45.0

julia> rad2deg(angle(1 - im))
-45.0

julia> rad2deg(angle(-1 + 1e-20im))
180.0

julia> rad2deg(angle(-1 - 1e-20im))
-180.0
```
