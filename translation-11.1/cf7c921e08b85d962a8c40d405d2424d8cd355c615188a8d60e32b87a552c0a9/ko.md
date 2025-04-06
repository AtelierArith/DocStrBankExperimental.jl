```
dlopen(libfile::AbstractString [, flags::Integer]; throw_error:Bool = true)
```

공유 라이브러리를 로드하고 불투명한 핸들을 반환합니다.

상수 `dlext`(`.so`, `.dll`, 또는 `.dylib`)로 주어진 확장자는 `libfile` 문자열에서 생략할 수 있으며, 필요할 경우 자동으로 추가됩니다. `libfile`이 절대 경로 이름이 아닌 경우, 배열 `DL_LOAD_PATH`의 경로에서 `libfile`을 검색한 후 시스템 로드 경로를 검색합니다.

선택적 플래그 인수는 `RTLD_LOCAL`, `RTLD_GLOBAL`, `RTLD_LAZY`, `RTLD_NOW`, `RTLD_NODELETE`, `RTLD_NOLOAD`, `RTLD_DEEPBIND`, 및 `RTLD_FIRST` 중 0개 이상의 비트 OR입니다. 이러한 플래그는 가능할 경우 POSIX(및/또는 GNU libc 및/또는 MacOS) dlopen 명령의 해당 플래그로 변환되거나, 현재 플랫폼에서 지정된 기능이 사용 불가능한 경우 무시됩니다. 기본 플래그는 플랫폼에 따라 다릅니다. MacOS에서 기본 `dlopen` 플래그는 `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`인 반면, 다른 플랫폼에서는 기본값이 `RTLD_LAZY|RTLD_DEEPBIND|RTLD_LOCAL`입니다. 이러한 플래그의 중요한 용도는 동적 라이브러리 로더가 라이브러리 참조를 내보낸 기호에 바인딩할 때 비기본 동작을 지정하고 바인딩된 참조가 프로세스 로컬 또는 전역 범위에 배치되는지 여부를 지정하는 것입니다. 예를 들어 `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`은 라이브러리의 기호가 다른 공유 라이브러리에서 사용 가능하도록 하여 공유 라이브러리 간의 의존성이 있는 상황을 해결합니다.

라이브러리를 찾을 수 없는 경우, 이 메서드는 오류를 발생시키며, 키워드 인수 `throw_error`가 `false`로 설정된 경우에는 이 메서드가 `nothing`을 반환합니다.

!!! note
    Julia 1.6부터 이 메서드는 `@executable_path/`로 시작하는 경로를 Julia 실행 파일의 경로로 대체하여 재배치 가능한 상대 경로 로드를 허용합니다. Julia 1.5 및 이전 버전에서는 macOS에서만 작동했습니다.

