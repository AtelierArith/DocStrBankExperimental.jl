```
Sys.CPU_THREADS::Int
```

시스템에서 사용 가능한 논리 CPU 코어의 수, 즉 CPU가 동시에 실행할 수 있는 스레드의 수입니다. 이는 반드시 CPU 코어의 수와 일치하지는 않으며, 예를 들어 [하이퍼 스레딩](https://en.wikipedia.org/wiki/Hyper-threading)이 있는 경우가 있습니다.

물리적 코어 수를 포함한 추가 정보는 Hwloc.jl 또는 CpuId.jl을 참조하십시오.
