```
LibGit2.Buffer
```

libgit2에서 데이터를 내보내기 위한 데이터 버퍼입니다. [`git_buf`](https://libgit2.org/libgit2/#HEAD/type/git_buf) 구조체와 일치합니다.

LibGit2에서 데이터를 가져올 때 일반적인 사용 예는 다음과 같습니다:

```julia
buf_ref = Ref(Buffer())
@check ccall(..., (Ptr{Buffer},), buf_ref)
# buf_ref에 대한 작업
free(buf_ref)
```

특히, `Ref` 객체에 대해 이후에 `LibGit2.free`를 호출해야 한다는 점에 유의하십시오.
