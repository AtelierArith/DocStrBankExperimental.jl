```
commit(repo::GitRepo, msg::AbstractString; kwargs...) -> GitHash
```

[`git_commit_create`](https://libgit2.org/libgit2/#HEAD/group/commit/git_commit_create)를 감싸는 함수입니다. `repo`에 커밋을 생성합니다. `msg`는 커밋 메시지입니다. 새 커밋의 OID를 반환합니다.

키워드 인자는 다음과 같습니다:

  * `refname::AbstractString=Consts.HEAD_FILE`: NULL이 아닌 경우, 새 커밋을 가리키도록 업데이트할 참조의 이름입니다. 예를 들어, `"HEAD"`는 현재 브랜치의 HEAD를 업데이트합니다. 참조가 아직 존재하지 않으면 생성됩니다.
  * `author::Signature = Signature(repo)`는 커밋을 작성한 사람에 대한 정보를 포함하는 `Signature`입니다.
  * `committer::Signature = Signature(repo)`는 커밋을 저장소에 커밋한 사람에 대한 정보를 포함하는 `Signature`입니다. 반드시 `author`와 동일할 필요는 없으며, 예를 들어 `author`가 패치를 이메일로 `committer`에게 보내고 `committer`가 이를 커밋한 경우입니다.
  * `tree_id::GitHash = GitHash()`는 커밋을 생성하는 데 사용할 git 트리로, 그 조상 및 다른 역사와의 관계를 보여줍니다. `tree`는 `repo`에 속해야 합니다.
  * `parent_ids::Vector{GitHash}=GitHash[]`는 새 커밋의 부모 커밋으로 사용할 [`GitHash`](@ref) 커밋 목록이며, 비어 있을 수 있습니다. 커밋은 예를 들어 병합 커밋인 경우 여러 부모를 가질 수 있습니다.
