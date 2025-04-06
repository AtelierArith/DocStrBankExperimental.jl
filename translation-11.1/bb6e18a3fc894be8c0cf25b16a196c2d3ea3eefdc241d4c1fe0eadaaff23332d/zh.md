```
committer(c::GitCommit)
```

返回提交 `c` 的提交者的 `Signature`。提交者是最初由 [`author`](@ref) 创作的更改的提交人，但不必与 `author` 相同，例如，如果 `author` 将补丁通过电子邮件发送给提交者，而提交者进行了提交。
