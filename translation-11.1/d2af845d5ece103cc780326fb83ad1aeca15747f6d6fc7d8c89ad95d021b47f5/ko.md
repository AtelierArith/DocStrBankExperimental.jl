```
Pipe()
```

초기화되지 않은 Pipe 객체를 생성합니다. 이는 여러 프로세스 간의 IO 통신을 위해 특별히 설계되었습니다.

파이프의 적절한 끝은 프로세스 생성에 객체가 사용될 경우 자동으로 초기화됩니다. 이는 프로세스 파이프라인에서 참조를 쉽게 얻는 데 유용할 수 있습니다. 예를 들어:

```
julia> err = Pipe()

# 이 후 `err`는 초기화되며, `err` 파이프에서 `foo`의
# stderr를 읽거나 `err`를 다른 파이프라인에 전달할 수 있습니다.
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)

# 이제 파이프의 쓰기 절반을 파괴하여 읽기 절반이 EOF를 받도록 합니다.
julia> closewrite(err)

julia> read(err, String)
"stderr messages"
```

자세한 내용은 [`Base.link_pipe!`](@ref)를 참조하세요.
