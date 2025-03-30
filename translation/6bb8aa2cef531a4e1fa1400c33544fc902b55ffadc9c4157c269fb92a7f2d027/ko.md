```
ccall((function_name, library), returntype, (argtype1, ...), argvalue1, ...)
ccall(function_name, returntype, (argtype1, ...), argvalue1, ...)
ccall(function_pointer, returntype, (argtype1, ...), argvalue1, ...)
```

C에서 내보낸 공유 라이브러리의 함수를 호출합니다. `(function_name, library)` 튜플로 지정되며, 각 구성 요소는 문자열 또는 기호일 수 있습니다. 라이브러리를 지정하는 대신, 현재 프로세스에서 해결되는 `function_name` 기호 또는 문자열을 사용할 수도 있습니다. 또는 `ccall`을 사용하여 `dlsym`에 의해 반환된 함수 포인터 `function_pointer`를 호출할 수도 있습니다.

인수 유형 튜플은 리터럴 튜플이어야 하며, 튜플 값을 가진 변수나 표현식이 아니어야 합니다.

`ccall`에 대한 각 `argvalue`는 자동으로 `unsafe_convert(argtype, cconvert(argtype, argvalue))` 호출을 삽입하여 해당 `argtype`으로 변환됩니다. (자세한 내용은 [`unsafe_convert`](@ref Base.unsafe_convert) 및 [`cconvert`](@ref Base.cconvert) 문서를 참조하십시오.) 대부분의 경우, 이는 단순히 `convert(argtype, argvalue)` 호출로 이어집니다.
