```
set_num_threads(n::Integer)
set_num_threads(::Nothing)
```

BLAS 라이브러리가 사용할 스레드 수를 `n::Integer`와 같게 설정합니다.

또한 `nothing`을 허용하며, 이 경우 줄리아는 기본 스레드 수를 추측하려고 시도합니다. `nothing`을 전달하는 것은 권장되지 않으며 주로 역사적인 이유로 존재합니다.
