```
committer(c::GitCommit)
```

`c` commitinin imzacısını döndürür. İmza, [`author`](@ref) tarafından orijinal olarak yazılan değişiklikleri taahhüt eden kişidir, ancak `author` ile aynı olmak zorunda değildir; örneğin, `author` bir yamanın e-postasını bir `committer`'a gönderirse ve o da bunu taahhüt ederse.
