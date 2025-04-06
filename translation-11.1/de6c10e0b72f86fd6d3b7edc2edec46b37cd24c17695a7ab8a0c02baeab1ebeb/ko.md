```
write(io::IO, x)
```

주어진 I/O 스트림 또는 파일에 값의 표준 이진 표현을 씁니다. 스트림에 기록된 바이트 수를 반환합니다. 텍스트 표현을 쓰려면 [`print`](@ref)를 참조하세요 (인코딩은 `io`에 따라 달라질 수 있습니다).

작성된 값의 바이트 순서는 호스트 시스템의 바이트 순서에 따라 다릅니다. 일관된 결과를 얻기 위해 쓰기/읽기 시 고정 바이트 순서로 변환하세요 (예: [`htol`](@ref) 및 [`ltoh`](@ref) 사용).

같은 `write` 호출로 여러 값을 쓸 수 있습니다. 즉, 다음은 동등합니다:

```
write(io, x, y...)
write(io, x) + write(io, y...)
```

# 예제

일관된 직렬화:

```jldoctest
julia> fname = tempname(); # 임의의 임시 파일 이름

julia> open(fname,"w") do f
           # 64비트 정수를 리틀 엔디안 바이트 순서로 기록합니다.
           write(f,htol(Int64(42)))
       end
8

julia> open(fname,"r") do f
           # 호스트 바이트 순서 및 호스트 정수 유형으로 변환합니다.
           Int(ltoh(read(f,Int64)))
       end
42
```

쓰기 호출 병합:

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang는 GitHub 조직입니다.", " 많은 구성원이 있습니다.")
56

julia> String(take!(io))
"JuliaLang는 GitHub 조직입니다. 많은 구성원이 있습니다."

julia> write(io, "가끔 그 구성원들이") + write(io, " 문서를 작성합니다.")
44

julia> String(take!(io))
"가끔 그 구성원들이 문서를 작성합니다."
```

`write` 메서드가 없는 사용자 정의 평범한 데이터 유형은 `Ref`로 감싸서 쓸 수 있습니다:

```jldoctest
julia> struct MyStruct; x::Float64; end

julia> io = IOBuffer()
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=Inf, ptr=1, mark=-1)

julia> write(io, Ref(MyStruct(42.0)))
8

julia> seekstart(io); read!(io, Ref(MyStruct(NaN)))
Base.RefValue{MyStruct}(MyStruct(42.0))
```
