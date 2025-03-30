```
LibGit2.create_branch(repo::GitRepo, bname::AbstractString, commit_obj::GitCommit; force::Bool=false)
```

`repo` deposunda `bname` adıyla yeni bir dal oluşturur ve bu dal `commit_obj`'a işaret eder (bu, `repo`nun bir parçası olmalıdır). Eğer `force` `true` ise, mevcutsa `bname` adındaki bir dalı üzerine yazar. Eğer `force` `false` ise ve zaten `bname` adında bir dal mevcutsa, bu fonksiyon bir hata fırlatacaktır.
