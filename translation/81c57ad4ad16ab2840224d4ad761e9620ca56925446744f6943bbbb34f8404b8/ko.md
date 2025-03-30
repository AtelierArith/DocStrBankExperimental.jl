```
Base.depwarn(msg::String, funcsym::Symbol; force=false)
```

`msg`를 비추천 경고로 출력합니다. 기호 `funcsym`은 호출 함수의 이름이어야 하며, 이는 각 호출 위치에 대해 비추천 경고가 처음 한 번만 출력되도록 보장하는 데 사용됩니다. `force=true`로 설정하면 Julia가 `--depwarn=no`(기본값)로 시작되었더라도 경고가 항상 표시되도록 강제합니다.

자세한 내용은 [`@deprecate`](@ref)를 참조하세요.

# 예제

```julia
function deprecated_func()
    Base.depwarn("Don't use `deprecated_func()`!", :deprecated_func)

    1 + 1
end
```
