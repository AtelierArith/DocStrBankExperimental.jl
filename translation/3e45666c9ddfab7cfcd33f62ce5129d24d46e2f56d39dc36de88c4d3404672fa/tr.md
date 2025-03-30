```
treewalk(f, tree::GitTree, post::Bool=false)
```

`tree` içindeki ve alt ağaçlarındaki girişleri post veya pre sırasına göre gezmek için kullanılır. Preorder, kökten başlayarak en soldaki alt ağaca geçmek (ve o alt ağacın en soldaki alt ağaçları boyunca özyinelemeli olarak devam etmek) ve alt ağaçlar boyunca sağa doğru hareket etmek anlamına gelir. Postorder ise en soldaki alt ağacın en altından başlayarak yukarı doğru geçmek, ardından bir sonraki sağ alt ağacı (yine en alttan başlayarak) gezmek ve en son olarak ağaç kökünü ziyaret etmek anlamına gelir.

Fonksiyon parametresi `f` aşağıdaki imzaya sahip olmalıdır:

```
(String, GitTreeEntry) -> Cint
```

`f`'den dönen negatif bir değer ağaç yürüyüşünü durdurur. Pozitif bir değer, `post` `false` ise girişin atlanacağı anlamına gelir.
