```
undocumented_names(mod::Module; private=false)
```

문서화되지 않은 기호의 정렬된 벡터를 반환합니다 `module` (즉, 문서 문자열이 없는). `private=false` (기본값)은 `public` 및/또는 `export`로 선언된 식별자만 반환하고, `private=true`는 모듈의 모든 기호를 반환합니다 (컴파일러가 생성한 `#`로 시작하는 숨겨진 기호는 제외).

참고: [`names`](@ref), [`Docs.hasdoc`](@ref), [`Base.ispublic`](@ref).
