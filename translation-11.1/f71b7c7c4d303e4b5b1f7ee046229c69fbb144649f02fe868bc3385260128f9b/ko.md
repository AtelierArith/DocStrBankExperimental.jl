```
IOContext(io::IO, KV::Pair...)
```

주어진 스트림을 감싸는 `IOContext`를 생성하고, 해당 스트림의 속성에 지정된 `key=>value` 쌍을 추가합니다 (note that `io` can itself be an `IOContext`).

  * `(key => value) in io`를 사용하여 이 특정 조합이 속성 집합에 있는지 확인합니다.
  * `get(io, key, default)`를 사용하여 특정 키에 대한 가장 최근 값을 검색합니다.

다음 속성은 일반적으로 사용됩니다:

  * `:compact`: 값이 더 간결하게 출력되어야 함을 지정하는 Boolean입니다. 예를 들어, 숫자가 더 적은 자릿수로 출력되어야 합니다. 이는 배열 요소를 출력할 때 설정됩니다. `:compact` 출력에는 줄 바꿈이 포함되지 않아야 합니다.
  * `:limit`: 컨테이너가 잘려야 함을 지정하는 Boolean입니다. 예를 들어, 대부분의 요소 대신 `…`를 표시합니다.
  * `:displaysize`: 텍스트 출력을 위해 사용할 행과 열의 크기를 제공하는 `Tuple{Int,Int}`입니다. 이는 호출된 함수의 표시 크기를 재정의하는 데 사용할 수 있지만, 화면의 크기를 얻으려면 `displaysize` 함수를 사용해야 합니다.
  * `:typeinfo`: 표시될 객체의 유형에 대해 이미 인쇄된 정보를 특성화하는 `Type`입니다. 이는 동일한 유형의 객체 모음을 표시할 때 주로 유용하여 중복된 유형 정보를 피할 수 있습니다 (예: `[Float16(0)]`는 "Float16[0.0]"으로 표시될 수 있으며, "Float16[Float16(0.0)]" 대신에 배열의 요소를 표시할 때 `:typeinfo` 속성은 `Float16`으로 설정됩니다).
  * `:color`: ANSI 색상/이스케이프 코드가 지원/예상되는지를 지정하는 Boolean입니다. 기본적으로 이는 `io`가 호환 가능한 터미널인지와 `julia`가 시작될 때의 `--color` 명령줄 플래그에 의해 결정됩니다.

# 예제

```jldoctest
julia> io = IOBuffer();

julia> printstyled(IOContext(io, :color => true), "string", color=:red)

julia> String(take!(io))
"\e[31mstring\e[39m"

julia> printstyled(io, "string", color=:red)

julia> String(take!(io))
"string"
```

```jldoctest
julia> print(IOContext(stdout, :compact => false), 1.12341234)
1.12341234
julia> print(IOContext(stdout, :compact => true), 1.12341234)
1.12341
```

```jldoctest
julia> function f(io::IO)
           if get(io, :short, false)
               print(io, "short")
           else
               print(io, "loooooong")
           end
       end
f (generic function with 1 method)

julia> f(stdout)
loooooong
julia> f(IOContext(stdout, :short => true))
short
```
