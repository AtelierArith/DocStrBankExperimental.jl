# I/O and Network

## General I/O

```@docs
Base.stdout
Base.stderr
Base.stdin
Base.read(::AbstractString)
Base.write(::AbstractString, ::Any)
Base.open
Base.IOStream
Base.IOBuffer
Base.take!(::Base.GenericIOBuffer)
Base.Pipe
Base.link_pipe!
Base.fdio
Base.flush
Base.close
Base.closewrite
Base.write
Base.read
Base.read!
Base.readbytes!
Base.unsafe_read
Base.unsafe_write
Base.readeach
Base.peek
Base.position
Base.seek
Base.seekstart
Base.seekend
Base.skip
Base.mark
Base.unmark
Base.reset(::IO)
Base.ismarked
Base.eof
Base.isreadonly
Base.iswritable
Base.isreadable
Base.isexecutable
Base.isopen
Base.fd
Base.redirect_stdio
Base.redirect_stdout
Base.redirect_stdout(::Function, ::Any)
Base.redirect_stderr
Base.redirect_stderr(::Function, ::Any)
Base.redirect_stdin
Base.redirect_stdin(::Function, ::Any)
Base.readchomp
Base.truncate
Base.skipchars
Base.countlines
Base.PipeBuffer
Base.readavailable
Base.IOContext
Base.IOContext(::IO, ::Pair)
Base.IOContext(::IO, ::IOContext)
```

## Text I/O

```@docs
Base.show(::IO, ::Any)
Base.summary
Base.print
Base.println
Base.printstyled
Base.sprint
Base.showerror
Base.dump
Meta.@dump
Base.readline
Base.readuntil
Base.readlines
Base.eachline
Base.copyline
Base.copyuntil
Base.displaysize
```

## [Multimedia I/O](@id Multimedia-I/O)

[`print`](@ref)에 의해 텍스트 출력이 수행되는 것처럼, 사용자 정의 유형은 [`show`](@ref)를 오버로드하여 텍스트 표현을 나타낼 수 있습니다. Julia는 이미지, 서식 있는 텍스트, 심지어 오디오 및 비디오와 같은 풍부한 멀티미디어 출력을 위한 표준화된 메커니즘을 제공하며, 이는 세 가지 부분으로 구성됩니다:

  * 함수 [`display(x)`](@ref)는 평문 텍스트 대체를 사용하여 Julia 객체 `x`의 가장 풍부한 멀티미디어 디스플레이를 요청합니다.
  * [`show`](@ref)의 오버로딩은 사용자 정의 유형의 임의 멀티미디어 표현(표준 MIME 유형으로 키가 지정됨)을 나타낼 수 있게 해줍니다.
  * 멀티미디어 기능을 갖춘 디스플레이 백엔드는 일반 [`AbstractDisplay`](@ref) 유형을 서브클래싱하여 등록할 수 있으며, [`pushdisplay`](@ref)를 통해 디스플레이 백엔드 스택에 푸시할 수 있습니다.

기본 Julia 런타임은 일반 텍스트 표시만 제공하지만, 외부 모듈을 로드하거나 그래픽 Julia 환경(예: IPython 기반의 IJulia 노트북)을 사용하여 더 풍부한 표시를 활성화할 수 있습니다.

```@docs
Base.AbstractDisplay
Base.Multimedia.display
Base.Multimedia.redisplay
Base.Multimedia.displayable
Base.show(::IO, ::Any, ::Any)
Base.Multimedia.showable
Base.repr(::MIME, ::Any)
Base.MIME
Base.@MIME_str
```

위에서 언급한 바와 같이, 새로운 디스플레이 백엔드를 정의할 수도 있습니다. 예를 들어, PNG 이미지를 창에 표시할 수 있는 모듈은 이 기능을 줄리아에 등록할 수 있으며, PNG 표현을 가진 타입에 대해 [`display(x)`](@ref)를 호출하면 모듈의 창을 사용하여 자동으로 이미지를 표시합니다.

새로운 디스플레이 백엔드를 정의하기 위해서는 먼저 추상 클래스 [`AbstractDisplay`](@ref)의 하위 유형 `D`를 생성해야 합니다. 그런 다음 `D`에서 표시할 수 있는 각 MIME 유형(`mime` 문자열)에 대해 `display(d::D, ::MIME"mime", x) = ...` 함수를 정의하여 `x`를 해당 MIME 유형으로 표시해야 합니다. 일반적으로 이는 [`show(io, mime, x)`](@ref) 또는 [`repr(io, mime, x)`](@ref)를 호출함으로써 이루어집니다. `x`를 해당 MIME 유형으로 표시할 수 없는 경우 [`MethodError`](@ref)가 발생해야 하며, 이는 `show` 또는 `repr`을 호출할 경우 자동으로 발생합니다. 마지막으로, `display(d::D, x)` 함수를 정의하여 [`showable(mime, x)`](@ref)에 대해 `D`가 지원하는 `mime` 유형을 쿼리하고 "최적의" 하나를 표시해야 합니다. `x`에 대해 지원되는 MIME 유형이 발견되지 않으면 `MethodError`가 발생해야 합니다. 유사하게, 일부 하위 유형은 [`redisplay(d::D, ...)`](@ref Base.Multimedia.redisplay)를 재정의하고 싶어할 수 있습니다. (다시 말해, 새로운 메서드를 `display`에 추가하기 위해 `import Base.display`를 해야 합니다.) 이러한 함수의 반환 값은 구현에 따라 다를 수 있습니다(일부 경우에는 특정 유형의 디스플레이 "핸들"을 반환하는 것이 유용할 수 있습니다). 그런 다음 `D`에 대한 디스플레이 함수는 직접 호출할 수 있지만, 디스플레이 백엔드 스택에 새로운 디스플레이를 푸시함으로써 [`display(x)`](@ref)에서 자동으로 호출될 수도 있습니다.

```@docs
Base.Multimedia.pushdisplay
Base.Multimedia.popdisplay
Base.Multimedia.TextDisplay
Base.Multimedia.istextmime
```

## Network I/O

```@docs
Base.bytesavailable
Base.ntoh
Base.hton
Base.ltoh
Base.htol
Base.ENDIAN_BOM
```
