```
setcpuaffinity(original_command::Cmd, cpus) -> command::Cmd
```

`command`의 CPU 친화성을 CPU ID 목록(1 기반) `cpus`로 설정합니다. `cpus = nothing`을 전달하면 `original_command`에 CPU 친화성이 설정되어 있는 경우 이를 해제합니다.

이 함수는 Linux와 Windows에서만 지원됩니다. macOS에서는 libuv가 친화성 설정을 지원하지 않기 때문에 지원되지 않습니다.

!!! compat "Julia 1.8"
    이 함수는 최소한 Julia 1.8이 필요합니다.


# 예제

Linux에서는 `taskset` 명령줄 프로그램을 사용하여 `setcpuaffinity`가 어떻게 작동하는지 확인할 수 있습니다.

```julia
julia> run(setcpuaffinity(`sh -c 'taskset -p $$'`, [1, 2, 5]));
pid 2273's current affinity mask: 13
```

마스크 값 `13`은 첫 번째, 두 번째 및 다섯 번째 비트(가장 덜 중요한 위치에서 계산)가 켜져 있음을 반영합니다:

```julia
julia> 0b010011
0x13
```
