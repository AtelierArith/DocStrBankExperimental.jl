```
transact(f::Function, repo::GitRepo)
```

함수 `f`를 git 저장소 `repo`에 적용하며, `f`를 적용하기 전에 [`snapshot`](@ref)를 찍습니다. `f` 내에서 오류가 발생하면, [`restore`](@ref)를 사용하여 `repo`를 스냅샷 상태로 되돌립니다. 발생한 오류는 다시 발생하지만, `repo`의 상태는 손상되지 않습니다.
