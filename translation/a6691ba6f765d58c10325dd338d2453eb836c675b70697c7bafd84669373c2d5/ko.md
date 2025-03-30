```
addface!(name::Symbol => default::Face)
```

이름 `name`으로 새로운 얼굴을 생성합니다. 이 이름으로 이미 얼굴이 존재하지 않는 한, `default`는 `FACES``.default`와 (복사본) `FACES`.`current`에 추가되며, 현재 값이 반환됩니다.

얼굴 `name`이 이미 존재하는 경우, `nothing`이 반환됩니다.

# 예시

```jldoctest; setup = :(import StyledStrings: Face, addface!)
julia> addface!(:mypkg_myface => Face(slant=:italic, underline=true))
Face (sample)
         slant: italic
     underline: true
```
