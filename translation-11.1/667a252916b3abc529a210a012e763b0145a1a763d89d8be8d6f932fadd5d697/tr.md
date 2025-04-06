```
disable_logging(level)
```

`level` seviyesine eşit veya daha düşük log seviyelerindeki tüm log mesajlarını devre dışı bırakır. Bu, devre dışı bırakıldığında hata ayıklama loglamasını son derece ucuz hale getirmek için tasarlanmış *küresel* bir ayardır.

# Örnekler

```julia
Logging.disable_logging(Logging.Info) # Hata ayıklama ve bilgi loglamasını devre dışı bırak
```
