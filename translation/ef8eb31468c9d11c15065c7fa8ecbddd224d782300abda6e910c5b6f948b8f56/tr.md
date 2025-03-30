```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

Pid dosyamızın formatını ayrıştırmayı deneyin, başarısız olan her okuma için sırasıyla (0, "", 0.0) ile bir öğeyi değiştirdik.
