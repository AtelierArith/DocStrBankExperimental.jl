```
withfaces(f, kv::Pair...)
withfaces(f, kvpair_itr)
```

`f`를 `FACES``.current`가 0개 이상의 `:name => val` 인수 `kv` 또는 `kv` 형식의 값을 생성하는 `kvpair_itr`에 의해 일시적으로 수정된 상태에서 실행합니다.

`withfaces`는 일반적으로 `withfaces(kv...) do ... end` 구문을 통해 사용됩니다. `nothing` 값은 얼굴을 일시적으로 해제하는 데 사용할 수 있습니다(설정된 경우). `withfaces`가 반환되면 원래의 `FACES``.current`가 복원됩니다.

# 예제

```jldoctest; setup = :(import StyledStrings: Face, withfaces)
julia> withfaces(:yellow => Face(foreground=:red), :green => :blue) do
           println(styled"{yellow:red} and {green:blue} mixed make {magenta:purple}")
       end
red and blue mixed make purple
```
