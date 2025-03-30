```
LAPACK异常
```

在直接调用[LAPACK函数](@ref man-linalg-lapack-functions)或调用其他内部使用LAPACK函数但缺乏专门错误处理的函数时抛出的通用LAPACK异常。`info`字段包含有关基础错误的附加信息，并取决于被调用的LAPACK函数。
