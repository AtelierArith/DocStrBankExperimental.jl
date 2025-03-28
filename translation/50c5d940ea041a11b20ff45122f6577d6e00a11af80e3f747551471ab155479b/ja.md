```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

注釈付きのgitコミットは、どのように検索され、なぜそのように検索されたのかに関する情報を持っているため、リベースやマージ操作がコミットのコンテキストに関するより多くの情報を持つことができます。たとえば、競合しているマージのソース/ターゲットブランチに関する情報を含む競合ファイルがあります。注釈付きコミットは、たとえば[`FetchHead`](@ref)が渡されたときのリモートブランチの先端や、`GitReference`を使用して説明されたブランチの先端を参照することができます。
