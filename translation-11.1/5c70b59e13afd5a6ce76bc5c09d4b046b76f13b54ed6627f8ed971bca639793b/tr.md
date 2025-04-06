```
lock(lock)
```

`lock` mevcut olduğunda onu edin. Eğer `lock` başka bir görev/işlem tarafından zaten kilitlenmişse, mevcut hale gelmesini bekleyin.

Her `lock`, bir [`unlock`](@ref) ile eşleşmelidir.
