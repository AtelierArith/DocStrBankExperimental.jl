```
merge!(repo::GitRepo; kwargs...) -> Bool
```

`repo` üzerindeki bir git birleştirmesi gerçekleştirir, dalgalanan geçmişe sahip olan commit'leri mevcut dal ile birleştirir. Birleştirme başarılı olursa `true`, aksi takdirde `false` döner.

Anahtar argümanlar şunlardır:

  * `committish::AbstractString=""`: `committish` içindeki belirtilen commit'leri birleştir.
  * `branch::AbstractString=""`: `branch` dalını ve mevcut dal ile ayrıldığı andan itibaren tüm commit'lerini birleştir.
  * `fastforward::Bool=false`: Eğer `fastforward` `true` ise, yalnızca birleştirme bir hızlı ileri (mevcut dal başı birleştirilecek commit'lerin atasıdır) ise birleştir, aksi takdirde birleştirmeyi reddet ve `false` döndür. Bu, git CLI seçeneği `--ff-only` ile eşdeğerdir.
  * `merge_opts::MergeOptions=MergeOptions()`: `merge_opts`, çatışma durumunda birleştirme stratejisi gibi birleştirme için seçenekleri belirtir.
  * `checkout_opts::CheckoutOptions=CheckoutOptions()`: `checkout_opts`, kontrol adımı için seçenekleri belirtir.

Eşdeğer olarak `git merge [--ff-only] [<committish> | <branch>]`.

!!! not
    Eğer bir `branch` belirtirseniz, bu referans formatında yapılmalıdır, çünkü dize bir `GitReference`'a dönüştürülecektir. Örneğin, `branch_a` dalını birleştirmek istiyorsanız, `merge!(repo, branch="refs/heads/branch_a")` şeklinde çağırmalısınız.

