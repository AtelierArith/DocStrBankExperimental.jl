```
define_editor(fn, pattern; wait=false)
```

`pattern`에 맞는 새로운 편집기를 정의하여 `fn`을 사용하여 파일(특정 행 번호에서 열 수 있음)을 열 수 있습니다.

`fn` 인자는 주어진 편집기로 파일을 여는 방법을 결정하는 함수입니다. 다음과 같은 네 개의 인자를 받아야 합니다:

  * `cmd` - 편집기를 위한 기본 명령 객체
  * `path` - 열 파일의 경로
  * `line` - 편집기를 열 행 번호
  * `column` - 편집기를 열 열 번호

특정 명령으로 특정 행이나 특정 열을 열 수 없는 편집기는 `line` 및/또는 `column` 인자를 무시할 수 있습니다. `fn` 콜백은 파일을 열기 위한 적절한 `Cmd` 객체를 반환하거나 이 파일을 편집할 수 없음을 나타내기 위해 `nothing`을 반환해야 합니다. 이 편집기가 현재 환경에 적합하지 않음을 나타내기 위해 `nothing`을 사용하고 다른 편집기를 시도해야 합니다. 외부 명령을 생성할 필요가 없는 보다 일반적인 편집 후크를 추가하려면 콜백을 벡터 `EDITOR_CALLBACKS`에 직접 푸시할 수 있습니다.

`pattern` 인자는 문자열, 정규 표현식 또는 문자열과 정규 표현식의 배열입니다. `fn`이 호출되려면 패턴 중 하나가 `EDITOR`, `VISUAL` 또는 `JULIA_EDITOR`의 값을 일치해야 합니다. 문자열의 경우, 문자열은 편집기 명령의 첫 번째 단어의 [`basename`](@ref)과 같아야 하며, 확장자가 있는 경우 제거해야 합니다. 예를 들어, "vi"는 "vim -g"와 일치하지 않지만 "/usr/bin/vi -m"과 일치합니다. 또한 `vi.exe`와도 일치합니다. `pattern`이 정규 표현식인 경우, 모든 편집기 명령을 셸 이스케이프된 문자열로 비교합니다. 배열 패턴은 그 항목 중 하나라도 일치하면 일치합니다. 여러 편집기가 일치하는 경우, 가장 최근에 추가된 것이 사용됩니다.

기본적으로 줄리아는 편집기가 닫힐 때까지 기다리지 않고 백그라운드에서 실행합니다. 그러나 편집기가 터미널 기반인 경우, `wait=true`로 설정하는 것이 좋으며, 줄리아는 편집기가 닫힐 때까지 기다립니다.

편집기 환경 변수 중 하나가 설정되어 있지만 일치하는 편집기 항목이 없는 경우 기본 편집기 항목이 호출됩니다:

```
(cmd, path, line, column) -> `$cmd $path`
```

많은 편집기가 이미 정의되어 있다는 점에 유의하세요. 다음의 모든 명령은 이미 작동해야 합니다:

  * emacs
  * emacsclient
  * vim
  * nvim
  * nano
  * micro
  * kak
  * helix
  * textmate
  * mate
  * kate
  * subl
  * atom
  * notepad++
  * Visual Studio Code
  * open
  * pycharm
  * bbedit

# 예제

다음은 터미널 기반 `emacs`의 사용을 정의합니다:

```
define_editor(
    r"\bemacs\b.*\s(-nw|--no-window-system)\b", wait=true) do cmd, path, line
    `$cmd +$line $path`
end
```

!!! compat "Julia 1.4"
    `define_editor`는 Julia 1.4에서 도입되었습니다.

