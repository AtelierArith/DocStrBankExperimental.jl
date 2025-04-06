```
rewrite(
    [ predicate, ] old_tarball, [ new_tarball ];
    [ portable = false, ]
) -> new_tarball

    predicate   :: Header --> Bool
    old_tarball :: Union{AbstractString, AbstractCmd, IO}
    new_tarball :: Union{AbstractString, AbstractCmd, IO}
    portable    :: Bool
```

`old_tarball`을 `create`가 생성하는 표준 형식으로 다시 작성하면서, `extract`가 오류를 발생시키는 원인이 되는 내용을 포함하지 않도록 확인합니다. 이는 기능적으로 다음과 같습니다.

```
Tar.create(Tar.extract(predicate, old_tarball), new_tarball)
```

그러나, 디스크에 아무것도 추출하지 않고 대신 `seek` 함수를 사용하여 이전 tarball의 데이터를 탐색합니다. `new_tarball` 인수가 전달되지 않으면, 새로운 tarball은 경로가 반환되는 임시 파일에 작성됩니다.

`predicate` 함수가 전달되면, `old_tarball`을 추출하는 동안 만나는 각 `Header` 객체에 대해 호출되며, `predicate(hdr)`가 true가 아닌 경우 항목은 건너뜁니다. 이는 아카이브의 일부만 선택적으로 다시 작성하거나, `extract`가 오류를 발생시키는 항목을 건너뛰거나, 다시 작성 과정에서 만나는 내용을 기록하는 데 사용할 수 있습니다.

`predicate` 함수에 전달되기 전에 `Header` 객체는 tarball의 원시 헤더에서 다소 수정됩니다: `path` 필드는 `.` 항목을 제거하고 여러 개의 연속 슬래시를 단일 슬래시로 대체하도록 정규화됩니다. 항목의 유형이 `:hardlink`인 경우, 링크 대상 경로도 동일한 방식으로 정규화되어 대상 항목의 경로와 일치하도록 합니다. 크기 필드는 대상 경로의 크기로 설정됩니다(이미 본 파일이어야 함).

`portable` 플래그가 true인 경우, 경로 이름이 Windows에서 유효성을 검사하여 불법 문자가 포함되지 않거나 예약된 이름이 없도록 합니다. 자세한 내용은 https://stackoverflow.com/a/31976060/659248을 참조하십시오.
