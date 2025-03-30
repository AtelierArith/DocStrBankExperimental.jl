```
LogLevel(level)
```

Bir log kaydının ciddiyeti/ayrıntı seviyesi.

Log seviyesi, potansiyel log kayıtlarının filtrelenebileceği bir anahtar sağlar; bu, log kaydı veri yapısını oluşturmak için başka bir iş yapılmadan önce gerçekleşir.

# Örnekler

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
