```
@ccall library.function_name(argvalue1::argtype1, ...)::returntype
@ccall function_name(argvalue1::argtype1, ...)::returntype
@ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

C에서 내보낸 공유 라이브러리의 함수를 호출합니다. 여기서 `library.function_name`은 문자열 상수 또는 리터럴입니다. 라이브러리는 생략할 수 있으며, 이 경우 `function_name`은 현재 프로세스에서 해결됩니다. 또는 `@ccall`을 사용하여 `dlsym`에 의해 반환된 함수 포인터 `$function_pointer`를 호출할 수도 있습니다.

각 `argvalue`는 자동으로 `unsafe_convert(argtype, cconvert(argtype, argvalue))` 호출을 삽입하여 해당 `argtype`으로 변환됩니다. (자세한 내용은 [`unsafe_convert`](@ref Base.unsafe_convert) 및 [`cconvert`](@ref Base.cconvert) 문서를 참조하십시오.) 대부분의 경우, 이는 단순히 `convert(argtype, argvalue)` 호출로 이어집니다.

# 예제

```
@ccall strlen(s::Cstring)::Csize_t
```

이는 C 표준 라이브러리 함수를 호출합니다:

```
size_t strlen(char *)
```

여기서 `s`라는 이름의 Julia 변수를 사용합니다. `ccall`도 참조하십시오.

가변 인자는 다음과 같은 규칙으로 지원됩니다:

```
@ccall printf("%s = %d"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
```

세미콜론은 필수 인수(최소 하나 이상이어야 함)와 가변 인수를 구분하는 데 사용됩니다.

외부 라이브러리를 사용하는 예:

```
# g_uri_escape_string의 C 시그니처:
# char *g_uri_escape_string(const char *unescaped, const char *reserved_chars_allowed, gboolean allow_utf8);

const glib = "libglib-2.0"
@ccall glib.g_uri_escape_string(my_uri::Cstring, ":/"::Cstring, true::Cint)::Cstring
```

문자열 리터럴은 원할 경우 함수 이름 앞에 직접 사용할 수도 있습니다 `"libglib-2.0".g_uri_escape_string(...`
