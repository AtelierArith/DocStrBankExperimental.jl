```
DateTime
```

`DateTime`은 프로레프틱 그레고리력에 따라 시간의 한 지점을 나타냅니다. 시간의 가장 세밀한 해상도는 밀리초입니다(즉, 마이크로초나 나노초는 이 유형으로 표현할 수 없습니다). 이 유형은 고정 소수점 산술을 지원하므로 언더플로우(및 오버플로우)에 취약합니다. 주목할 만한 결과는 `Microsecond` 또는 `Nanosecond`를 더할 때 반올림이 발생하는 것입니다:

```jldoctest
julia> dt = DateTime(2023, 8, 19, 17, 45, 32, 900)
2023-08-19T17:45:32.900

julia> dt + Millisecond(1)
2023-08-19T17:45:32.901

julia> dt + Microsecond(1000) # 1000us == 1ms
2023-08-19T17:45:32.901

julia> dt + Microsecond(999) # 999us는 1000us로 반올림됨
2023-08-19T17:45:32.901

julia> dt + Microsecond(1499) # 1499는 1000us로 반올림됨
2023-08-19T17:45:32.901
```
