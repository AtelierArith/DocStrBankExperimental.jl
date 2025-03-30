```
LibGit2.rebase!(repo::GitRepo, upstream::AbstractString="", newbase::AbstractString="")
```

Mevcut dalın otomatik bir birleştirme rebase'ini `upstream` sağlanmışsa ondan, aksi takdirde yukarı akış izleme dalından denemektedir. `newbase`, üzerine rebase yapılacak dalı belirtir. Varsayılan olarak bu `upstream`'dir.

Eğer otomatik olarak çözülemeyen herhangi bir çelişki ortaya çıkarsa, rebase iptal edilecek ve depo ile çalışma ağacı orijinal durumunda kalacak ve fonksiyon bir `GitError` fırlatacaktır. Bu, aşağıdaki komut satırı ifadesine yaklaşık olarak eşdeğerdir:

```
git rebase --merge [<upstream>]
if [ -d ".git/rebase-merge" ]; then
    git rebase --abort
fi
```
