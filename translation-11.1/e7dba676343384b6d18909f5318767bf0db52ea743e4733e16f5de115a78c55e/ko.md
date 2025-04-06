```
redisplay(x)
redisplay(d::AbstractDisplay, x)
redisplay(mime, x)
redisplay(d::AbstractDisplay, mime, x)
```

기본적으로 `redisplay` 함수는 단순히 [`display`](@ref)를 호출합니다. 그러나 일부 디스플레이 백엔드는 기존의 `x` 디스플레이를 수정하기 위해 `redisplay`를 재정의할 수 있습니다(있는 경우). `redisplay`를 사용하는 것은 또한 백엔드에 `x`가 여러 번 다시 표시될 수 있음을 암시하며, 백엔드는 (예: 다음 대화형 프롬프트까지) 표시를 연기할 수 있습니다.
