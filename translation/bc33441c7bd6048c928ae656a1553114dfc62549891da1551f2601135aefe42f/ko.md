```
homedir() -> String
```

현재 사용자의 홈 디렉토리를 반환합니다.

!!! note
    `homedir`는 `libuv`의 `uv_os_homedir`를 통해 홈 디렉토리를 결정합니다. 홈 디렉토리를 환경 변수를 통해 지정하는 방법에 대한 자세한 내용은 [`uv_os_homedir` 문서](http://docs.libuv.org/en/v1.x/misc.html#c.uv_os_homedir)를 참조하세요.


또한 [`Sys.username`](@ref)를 참조하세요.
