```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

`pattern` içeren girişler için mevcut doküman dizelerini arayın.

`pattern` bir dize olduğunda, büyük/küçük harf dikkate alınmaz. Sonuçlar `io`'ya yazdırılır.

`apropos`, sorguyu çift tırnak içine alarak REPL'deki yardım modundan çağrılabilir:

```
help?> "pattern"
```
