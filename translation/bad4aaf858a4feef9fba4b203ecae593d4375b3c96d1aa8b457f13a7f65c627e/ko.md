```
extract(
    [ predicate, ] tarball, [ dir ];
    [ skeleton = <none>, ]
    [ copy_symlinks = <auto>, ]
    [ set_permissions = true, ]
) -> dir

    predicate       :: Header --> Bool
    tarball         :: Union{AbstractString, AbstractCmd, IO}
    dir             :: AbstractString
    skeleton        :: Union{AbstractString, AbstractCmd, IO}
    copy_symlinks   :: Bool
    set_permissions :: Bool
```

`tarball` 경로에 위치한 tar 아카이브를 `dir` 디렉토리로 추출합니다. `tarball`이 경로 대신 IO 객체인 경우, 아카이브 내용은 해당 IO 스트림에서 읽어옵니다. 아카이브는 `dir`로 추출되며, `dir`은 기존의 빈 디렉토리이거나 새 디렉토리로 생성할 수 있는 존재하지 않는 경로여야 합니다. `dir`이 지정되지 않으면, 아카이브는 임시 디렉토리에 추출되며, 이 임시 디렉토리는 `extract`에 의해 반환됩니다.

`predicate` 함수가 전달되면, `tarball`을 추출하는 동안 만나는 각 `Header` 객체에 대해 호출되며, 항목은 `predicate(hdr)`가 true일 때만 추출됩니다. 이는 아카이브의 일부만 선택적으로 추출하거나, `extract`가 오류를 발생시키는 항목을 건너뛰거나, 추출 과정에서 무엇이 추출되었는지를 기록하는 데 사용할 수 있습니다.

`Header` 객체는 predicate 함수에 전달되기 전에 tarball의 원시 헤더에서 다소 수정됩니다: `path` 필드는 `.` 항목을 제거하고 여러 개의 연속 슬래시를 단일 슬래시로 대체하도록 정규화됩니다. 항목의 유형이 `:hardlink`인 경우, 링크 대상 경로도 동일한 방식으로 정규화되어 대상 항목의 경로와 일치하게 됩니다; 크기 필드는 대상 경로의 크기로 설정됩니다(이미 본 파일이어야 함).

`skeleton` 키워드가 전달되면, 추출된 tarball의 "스켈레톤"이 주어진 파일 또는 IO 핸들에 기록됩니다. 이 스켈레톤 파일은 `create` 함수에 `skeleton` 키워드를 전달하여 동일한 tarball을 재생성하는 데 사용할 수 있습니다. `skeleton`과 `predicate` 인자는 함께 사용할 수 없습니다.

`copy_symlinks`가 `true`인 경우, 심볼릭 링크를 그대로 추출하는 대신, tarball 내부에 있고 가능할 경우 링크된 내용을 복사하여 추출됩니다. `/etc/passwd`와 같은 비내부 심볼릭 링크는 복사되지 않습니다. 어떤 식으로든 순환하는 심볼릭 링크도 복사되지 않으며 대신 건너뛰어집니다. 기본적으로, `extract`는 `dir`에서 심볼릭 링크를 생성할 수 있는지 여부를 감지하고, 생성할 수 없는 경우 자동으로 심볼릭 링크를 복사합니다.

`set_permissions`가 `false`인 경우, 추출된 파일에 대한 권한이 설정되지 않습니다.
