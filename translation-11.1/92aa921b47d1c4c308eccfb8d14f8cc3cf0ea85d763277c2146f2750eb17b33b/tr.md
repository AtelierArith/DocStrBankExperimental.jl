```
MultiSelectMenu
```

Bir kullanıcının bir listeden birden fazla seçenek seçmesine olanak tanıyan bir menü.

# Örnek Çıktı

```julia-repl
julia> request(MultiSelectMenu(options))
Sevdiğiniz meyveleri seçin:
[tuşla: Enter=değiştir, a=tümü, n=hiçbiri, d=tamam, q=iptal]
   [ ] elma
 > [X] portakal
   [X] üzüm
   [ ] çilek
   [ ] yaban mersini
   [X] şeftali
   [ ] limon
   [ ] lime
Sevdiğiniz meyveler:
  - portakal
  - üzüm
  - şeftali
```
