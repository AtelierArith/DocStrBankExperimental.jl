```
DateTime
```

`DateTime` 表示根据前瞻性格里高利历法的某个时间点。时间的最精细分辨率为毫秒（即，微秒或纳秒无法由此类型表示）。该类型支持定点算术，因此容易发生下溢（和上溢）。一个显著的后果是在添加 `Microsecond` 或 `Nanosecond` 时的舍入：

```jldoctest
julia> dt = DateTime(2023, 8, 19, 17, 45, 32, 900)
2023-08-19T17:45:32.900

julia> dt + Millisecond(1)
2023-08-19T17:45:32.901

julia> dt + Microsecond(1000) # 1000us == 1ms
2023-08-19T17:45:32.901

julia> dt + Microsecond(999) # 999us 舍入到 1000us
2023-08-19T17:45:32.901

julia> dt + Microsecond(1499) # 1499 舍入到 1000us
2023-08-19T17:45:32.901
```
