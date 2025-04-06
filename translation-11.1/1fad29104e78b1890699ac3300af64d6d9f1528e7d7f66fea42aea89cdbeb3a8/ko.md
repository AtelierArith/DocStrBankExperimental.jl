```
LibGit2.git_url(; kwargs...) -> String
```

제공된 URL 구성 요소를 기반으로 문자열을 생성합니다. `scheme` 키워드가 제공되지 않으면 생성된 URL은 대체 [scp 유사 구문](https://git-scm.com/docs/git-clone#_git_urls_a_id_urls_a)을 사용합니다.

# 키워드

  * `scheme::AbstractString=""`: 사용될 프로토콜을 식별하는 URL 스킴입니다. HTTP의 경우 "http", SSH의 경우 "ssh" 등을 사용합니다. `scheme`이 제공되지 않으면 출력 형식은 "ssh"가 되지만 scp 유사 구문을 사용합니다.
  * `username::AbstractString=""`: 제공된 경우 출력에 사용할 사용자 이름입니다.
  * `password::AbstractString=""`: 제공된 경우 출력에 사용할 비밀번호입니다.
  * `host::AbstractString=""`: 출력에 사용할 호스트 이름입니다. 호스트 이름은 반드시 지정해야 합니다.
  * `port::Union{AbstractString,Integer}=""`: 제공된 경우 출력에 사용할 포트 번호입니다. scp 유사 구문을 사용할 때는 지정할 수 없습니다.
  * `path::AbstractString=""`: 제공된 경우 출력에 사용할 경로입니다.

!!! 경고     URL에서 비밀번호 사용을 피하십시오. 자격 증명 객체와 달리, Julia는 사용 후 민감한 데이터를 안전하게 제로화하거나 파괴할 수 없으며 비밀번호가 메모리에 남아 있을 수 있습니다. 이는 초기화되지 않은 메모리에 의해 노출될 수 있습니다.

# 예제

```jldoctest
julia> LibGit2.git_url(username="git", host="github.com", path="JuliaLang/julia.git")
"git@github.com:JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="https", host="github.com", path="/JuliaLang/julia.git")
"https://github.com/JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="ssh", username="git", host="github.com", port=2222, path="JuliaLang/julia.git")
"ssh://git@github.com:2222/JuliaLang/julia.git"
```
