```
devnull
```

Wird in einer Stream-Umleitung verwendet, um alle Daten, die in ihn geschrieben werden, zu verwerfen. Entspricht im Wesentlichen `/dev/null` unter Unix oder `NUL` unter Windows. Verwendung:

```julia
run(pipeline(`cat test.txt`, devnull))
```
