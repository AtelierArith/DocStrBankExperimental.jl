```
Sys.CPU_THREADS::Int
```

Sistemde mevcut olan mantıksal CPU çekirdeklerinin sayısı, yani CPU'nun aynı anda çalıştırabileceği iş parçacığı sayısı. Bunun, örneğin [hyper-threading](https://en.wikipedia.org/wiki/Hyper-threading) varlığında, CPU çekirdeklerinin sayısı ile aynı olmayabileceğini unutmayın.

Fiziksel çekirdek sayısı da dahil olmak üzere daha fazla bilgi için Hwloc.jl veya CpuId.jl'ye bakın.
