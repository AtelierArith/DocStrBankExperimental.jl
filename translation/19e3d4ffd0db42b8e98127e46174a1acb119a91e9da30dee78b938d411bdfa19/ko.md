`Header` 타입은 tar 파일의 단일 레코드에 대한 필수 메타데이터를 나타내는 구조체로, 다음과 같은 정의를 가지고 있습니다:

```
struct Header
    path :: String # root에 대한 상대 경로
    type :: Symbol # 타입 표시기 (아래 참조)
    mode :: UInt16 # 모드/권한 (8진수로 보는 것이 가장 좋음)
    size :: Int64  # 레코드 데이터의 크기 (바이트 단위)
    link :: String # 심볼릭 링크의 대상 경로
end
```

타입은 다음 기호로 표현됩니다: `file`, `hardlink`, `symlink`, `chardev`, `blockdev`, `directory`, `fifo`, 또는 알 수 없는 타입의 경우 타입 플래그 문자를 기호로 사용합니다. [`extract`](@ref)는 `file`, `symlink` 및 `directory` 이외의 레코드 타입을 추출하는 것을 거부합니다; [`list`](@ref)는 `strict=false`로 호출될 경우 다른 종류의 레코드만 나열합니다.

tar 형식은 레코드에 대한 다양한 다른 메타데이터를 포함하며, 여기에는 사용자 및 그룹 ID, 사용자 및 그룹 이름, 타임스탬프가 포함됩니다. `Tar` 패키지는 설계상 이들을 완전히 무시합니다. tar 파일을 생성할 때, 이 필드는 항상 0/비어 있는 값으로 설정됩니다. tar 파일을 읽을 때, 이 필드는 모든 필드에 대해 각 헤더 레코드의 체크섬을 검증하는 것을 제외하고는 무시됩니다.
