```
LibGit2.GitRepoExt(path::AbstractString, flags::Cuint = Cuint(Consts.REPOSITORY_OPEN_DEFAULT))
```

`path` にある git リポジトリを拡張コントロールで開きます（たとえば、現在のユーザーが `path` を読み取るために特別なアクセスグループのメンバーである必要がある場合）。
