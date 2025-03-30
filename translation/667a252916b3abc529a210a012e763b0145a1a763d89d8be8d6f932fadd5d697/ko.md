```
disable_logging(level)
```

`level` 이하의 모든 로그 메시지를 비활성화합니다. 이는 디버그 로깅을 비활성화할 때 매우 저렴하게 만들기 위한 *전역* 설정입니다.

# 예제

```julia
Logging.disable_logging(Logging.Info) # 디버그 및 정보 비활성화
```
