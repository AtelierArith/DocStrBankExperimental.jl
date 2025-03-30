```
모듈
```

`모듈`은 별도의 전역 변수 작업 공간입니다. 자세한 내용은 [`module`](@ref) 및 [모듈에 대한 매뉴얼 섹션](@ref modules)을 참조하십시오.

```
Module(name::Symbol=:anonymous, std_imports=true, default_names=true)
```

지정된 이름으로 모듈을 반환합니다. `baremodule`은 `Module(:ModuleName, false)`에 해당합니다.

이름이 전혀 없는 빈 모듈은 `Module(:ModuleName, false, false)`로 생성할 수 있습니다. 이 모듈은 `Base` 또는 `Core`를 가져오지 않으며 자신에 대한 참조를 포함하지 않습니다.
