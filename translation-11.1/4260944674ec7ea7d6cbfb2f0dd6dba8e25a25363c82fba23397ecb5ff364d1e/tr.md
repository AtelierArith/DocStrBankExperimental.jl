```
merge_base(repo::GitRepo, one::AbstractString, two::AbstractString) -> GitHash
```

`one` ve `two` arasındaki ortak bir ata (birleştirme tabanı) bulun. `one` ve `two` her ikisi de string biçiminde olabilir. Birleştirme tabanının `GitHash`'ini döndürün.
