```
@time_imports
```

패키지와 그 의존성을 가져오는 데 소요된 시간을 보고하는 표현식을 실행하는 매크로입니다. 모든 컴파일 시간은 백분율로 보고되며, 재컴파일된 시간도 표시됩니다.

패키지 또는 패키지 확장마다 한 줄이 인쇄됩니다. 표시된 기간은 해당 패키지를 가져오는 데 걸린 시간이며, 그 의존성을 로드하는 데 걸린 시간은 포함되지 않습니다.

Julia 1.9+ [패키지 확장](@ref man-extensions)은 Parent → Extension으로 표시됩니다.

!!! note
    로드 과정에서 패키지는 직접적인 의존성뿐만 아니라 모든 의존성을 순차적으로 가져옵니다.


```julia-repl
julia> @time_imports using CSV
     50.7 ms  Parsers 17.52% compilation time
      0.2 ms  DataValueInterfaces
      1.6 ms  DataAPI
      0.1 ms  IteratorInterfaceExtensions
      0.1 ms  TableTraits
     17.5 ms  Tables
     26.8 ms  PooledArrays
    193.7 ms  SentinelArrays 75.12% compilation time
      8.6 ms  InlineStrings
     20.3 ms  WeakRefStrings
      2.0 ms  TranscodingStreams
      1.4 ms  Zlib_jll
      1.8 ms  CodecZlib
      0.8 ms  Compat
     13.1 ms  FilePathsBase 28.39% compilation time
   1681.2 ms  CSV 92.40% compilation time
```

!!! compat "Julia 1.8"
    이 매크로는 최소한 Julia 1.8이 필요합니다.

