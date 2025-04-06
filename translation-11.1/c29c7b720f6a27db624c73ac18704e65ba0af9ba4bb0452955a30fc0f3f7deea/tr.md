```
GitBlame(repo::GitRepo, path::AbstractString; options::BlameOptions=BlameOptions())
```

`path`'teki dosya için `repo`nun geçmişinden elde edilen değişiklik bilgilerini kullanarak bir `GitBlame` nesnesi oluşturur. `GitBlame` nesnesi, dosyanın hangi parçalarının ne zaman ve kim tarafından değiştirildiğini kaydeder. `options`, dosyanın içeriğini nasıl ayıracağınızı ve hangi commit'lerin inceleneceğini kontrol eder - daha fazla bilgi için [`BlameOptions`](@ref) bölümüne bakın.
