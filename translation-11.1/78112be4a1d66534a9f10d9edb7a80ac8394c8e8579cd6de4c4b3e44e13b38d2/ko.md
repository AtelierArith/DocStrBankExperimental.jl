```
create(
    [ predicate, ] dir, [ tarball ];
    [ skeleton, ] [ portable = false ]
) -> tarball

    predicate :: String --> Bool
    dir       :: AbstractString
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    skeleton  :: Union{AbstractString, AbstractCmd, IO}
    portable  :: Bool
```

디렉토리 `dir`의 tar 아카이브("tarball")를 생성합니다. 결과 아카이브는 `tarball` 경로에 기록되거나 경로가 지정되지 않은 경우 임시 경로가 생성되어 함수 호출에 의해 반환됩니다. `tarball`이 IO 객체인 경우 tarball 내용은 해당 핸들에 대신 기록됩니다(핸들은 열려 있습니다).

`predicate` 함수가 전달되면, 이는 `dir`을 재귀적으로 검색하는 동안 만나는 각 시스템 경로에 대해 호출되며, `predicate(path)`가 true인 경우에만 `path`가 tarball에 포함됩니다. `predicate(path)`가 디렉토리에 대해 false를 반환하면 해당 디렉토리는 완전히 제외됩니다: 해당 디렉토리 아래의 내용은 아카이브에 포함되지 않습니다.

`skeleton` 키워드가 전달되면, 주어진 파일 또는 IO 핸들이 tarball 생성을 위한 "스켈레톤"으로 사용됩니다. `extract` 명령에 `skeleton` 키워드를 전달하여 스켈레톤 파일을 생성합니다. 해당 스켈레톤 파일로 `create`가 호출되고 추출된 파일이 변경되지 않은 경우, 동일한 tarball이 재생성됩니다. `skeleton`과 `predicate` 인자는 함께 사용할 수 없습니다.

`portable` 플래그가 true인 경우, 경로 이름이 Windows에서 유효성을 검사하여 불법 문자가 포함되지 않거나 예약된 이름이 없도록 합니다. 자세한 내용은 https://stackoverflow.com/a/31976060/659248을 참조하십시오.
