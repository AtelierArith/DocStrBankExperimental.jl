```
LibGit2.StrArrayStruct
```

LibGit2의 문자열 배열 표현입니다. [`git_strarray`](https://libgit2.org/libgit2/#HEAD/type/git_strarray) 구조체와 일치합니다.

LibGit2에서 데이터를 가져올 때 일반적인 사용 예는 다음과 같습니다:

```julia
sa_ref = Ref(StrArrayStruct())
@check ccall(..., (Ptr{StrArrayStruct},), sa_ref)
res = convert(Vector{String}, sa_ref[])
free(sa_ref)
```

특히, `Ref` 객체에 대해 `LibGit2.free`를 호출해야 한다는 점에 유의하십시오.

반대로, 문자열 벡터를 LibGit2에 전달할 때는 일반적으로 암시적 변환에 의존하는 것이 가장 간단합니다:

```julia
strs = String[...]
@check ccall(..., (Ptr{StrArrayStruct},), strs)
```

데이터가 Julia에 의해 할당되므로 `free`를 호출할 필요가 없다는 점에 유의하십시오.
