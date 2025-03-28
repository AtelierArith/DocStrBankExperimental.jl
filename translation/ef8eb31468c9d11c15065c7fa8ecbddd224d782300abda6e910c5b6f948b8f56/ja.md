```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

私たちのpidfileフォーマットを解析しようとします。失敗した読み取りについては、それぞれ(0, "", 0.0)に置き換えられた要素があります。
