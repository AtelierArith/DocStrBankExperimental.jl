`HTML(s)`: `s`를 html로 렌더링하는 객체를 생성합니다.

```
HTML("<div>foo</div>")
```

대량의 데이터를 위해 스트림을 사용할 수도 있습니다:

```
HTML() do io
  println(io, "<div>foo</div>")
end
```

!!! 경고     `HTML`은 현재 이전 호환성을 유지하기 위해 내보내지고 있지만, 이 내보내기는 더 이상 권장되지 않습니다. 이 유형을 [`Docs.HTML`](@ref)로 사용하거나 `Docs`에서 명시적으로 가져오는 것이 좋습니다.
