```
RadyoMenü
```

Bir kullanıcının bir listedeki tek bir seçeneği seçmesine olanak tanıyan bir menü.

# Örnek Çıktı

```julia-repl
julia> request(RadioMenu(options, pagesize=4))
Favori meyvenizi seçin:
^  üzüm
   çilek
 > yaban mersini
v  şeftali
Favori meyveniz yaban mersini!
```
