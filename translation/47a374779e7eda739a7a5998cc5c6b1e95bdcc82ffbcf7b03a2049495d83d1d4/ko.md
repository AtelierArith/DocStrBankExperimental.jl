```
LibGit2.SignatureStruct
```

작업 서명(예: 커밋 작성자, 태그 작성자 등). [`git_signature`](https://libgit2.org/libgit2/#HEAD/type/git_signature) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `name`: 커밋 작성자 또는 커밋의 저자의 전체 이름.
  * `email`: 커밋 작성자/저자에게 연락할 수 있는 이메일.
  * `when`: 커밋이 저장소에 작성/커밋된 시간을 나타내는 [`TimeStruct`](@ref).
