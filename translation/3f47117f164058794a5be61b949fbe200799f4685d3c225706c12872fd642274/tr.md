```
Threads.maxthreadid() -> Int
```

Julia işlemi için mevcut olan (tüm iş parçacığı havuzları arasında) iş parçacığı sayısının alt sınırını atomic-acquire semantiği ile alın. Sonuç, her zaman [`threadid()`](@ref) ve `threadid(task)` için gözlemleyebildiğiniz herhangi bir görev için büyük veya eşit olacaktır.
