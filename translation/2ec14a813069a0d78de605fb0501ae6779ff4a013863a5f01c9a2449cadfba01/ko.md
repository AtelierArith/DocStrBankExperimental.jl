```
propertynames(x, private=false)
```

객체 `x`의 속성(`x.property`)의 튜플 또는 벡터를 가져옵니다. 이는 일반적으로 [`fieldnames(typeof(x))`](@ref)와 동일하지만, [`getproperty`](@ref)를 오버로드하는 타입은 일반적으로 `propertynames`도 오버로드하여 해당 타입의 인스턴스 속성을 가져와야 합니다.

`propertynames(x)`는 `x`의 문서화된 인터페이스의 일부인 "공개" 속성 이름만 반환할 수 있습니다. 내부 사용을 위한 "비공식" 속성 이름도 반환하려면 선택적 두 번째 인수로 `true`를 전달하십시오. `x.`에 대한 REPL 탭 완성은 `private=false` 속성만 표시합니다.

참고: [`hasproperty`](@ref), [`hasfield`](@ref).
