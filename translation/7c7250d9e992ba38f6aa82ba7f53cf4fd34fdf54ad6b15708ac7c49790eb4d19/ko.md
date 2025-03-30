```
open_exclusive(path::String; mode, poll_interval, wait, stale_age, refresh) :: File
```

읽기-쓰기 자문 전용 액세스를 위한 새 파일을 만듭니다. `wait`가 `false`이면 잠금 파일이 존재할 경우 오류를 발생시키고, 그렇지 않으면 잠금을 얻을 때까지 차단합니다.

키워드 인수에 대한 설명은 [`mkpidlock`](@ref)를 참조하십시오.
