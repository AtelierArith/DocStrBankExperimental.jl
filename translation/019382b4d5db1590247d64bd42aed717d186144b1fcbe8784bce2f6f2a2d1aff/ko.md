```
download(url, [ output = tempname() ];
    [ method = "GET", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ downloader = <default>, ]
) -> output

    url        :: AbstractString
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (total::Integer, now::Integer) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    downloader :: Downloader
```

주어진 url에서 파일을 다운로드하여 `output`에 저장하거나 지정되지 않은 경우 임시 경로에 저장합니다. `output`은 또한 `IO` 핸들이 될 수 있으며, 이 경우 응답의 본문이 해당 핸들로 스트리밍되고 핸들이 반환됩니다. `output`이 명령인 경우, 명령이 실행되고 출력이 stdin으로 전송됩니다.

`downloader` 키워드 인수가 제공되면, `Downloader` 객체여야 합니다. 리소스와 연결은 동일한 `Downloader`에 의해 수행된 다운로드 간에 공유되며, 객체가 가비지 수집될 때 자동으로 정리되거나 해당 객체로 수행된 다운로드가 없었던 경우 유예 기간이 지나면 정리됩니다. 구성 및 사용에 대한 자세한 내용은 `Downloader`를 참조하십시오.

`headers` 키워드 인수가 제공되면, 모든 요소가 문자열 쌍인 벡터 또는 사전이어야 합니다. 이러한 쌍은 HTTP/S와 같이 이를 지원하는 프로토콜로 URL을 다운로드할 때 헤더로 전달됩니다.

`timeout` 키워드 인수는 다운로드가 완료되는 데 걸리는 시간을 초 단위로 지정하며, 밀리초 단위의 해상도를 가집니다. 기본적으로 타임아웃이 설정되지 않지만, `Inf`의 타임아웃 값을 전달하여 명시적으로 요청할 수도 있습니다. 별도로, 20초가 경과하고 데이터가 수신되지 않으면 다운로드가 타임아웃됩니다. 이 타임아웃을 비활성화하는 방법에 대한 자세한 도움말을 참조하십시오.

`progress` 키워드 인수가 제공되면, 진행 중인 다운로드의 크기 및 상태에 대한 업데이트가 있을 때마다 호출되는 콜백 함수여야 합니다. 콜백은 두 개의 정수 인수인 `total`과 `now`를 받아야 하며, 이는 다운로드의 총 크기(바이트 단위)와 지금까지 다운로드된 바이트 수입니다. `total`은 처음에 0으로 시작하며, 서버가 다운로드의 총 크기를 나타내는 신호를 줄 때까지 0으로 유지됩니다(예: `Content-Length` 헤더로). 따라서 잘 동작하는 진행 콜백은 총 크기가 0인 경우를 우아하게 처리해야 합니다.

`verbose` 옵션이 true로 설정되면, 다운로드 기능을 구현하는 데 사용되는 `libcurl`이 `stderr`에 디버깅 정보를 출력합니다. `debug` 옵션이 두 개의 `String` 인수를 받는 함수로 설정되면, verbose 옵션은 무시되고 대신 `stderr`에 출력될 데이터가 `type` 및 `message` 인수와 함께 `debug` 콜백으로 전달됩니다. `type` 인수는 어떤 종류의 이벤트가 발생했는지를 나타내며, 다음 중 하나입니다: `TEXT`, `HEADER IN`, `HEADER OUT`, `DATA IN`, `DATA OUT`, `SSL DATA IN` 또는 `SSL DATA OUT`. `message` 인수는 디버그 이벤트에 대한 설명입니다.

## 확장 도움말

추가 사용자 지정을 위해 [`Downloader`](@ref) 및 [`easy_hook`s](https://github.com/JuliaLang/Downloads.jl#mutual-tls-using-downloads)를 사용하십시오. 예를 들어, 데이터가 수신되지 않을 때 20초 타임아웃을 비활성화하려면 다음을 사용할 수 있습니다:

```jl
downloader = Downloads.Downloader()
downloader.easy_hook = (easy, info) -> Downloads.Curl.setopt(easy, Downloads.Curl.CURLOPT_LOW_SPEED_TIME, 0)

Downloads.download("https://httpbingo.julialang.org/delay/30"; downloader)
```
