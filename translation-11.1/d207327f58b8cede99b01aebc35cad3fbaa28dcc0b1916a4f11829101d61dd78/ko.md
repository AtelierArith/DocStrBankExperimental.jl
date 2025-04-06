```
struct Response
    proto   :: String
    url     :: String
    status  :: Int
    message :: String
    headers :: Vector{Pair{String,String}}
end
```

`Response`는 요청에 대한 성공적인 응답의 속성을 객체로 캡처하는 타입입니다. 다음과 같은 필드를 가지고 있습니다:

  * `proto`: 응답을 얻기 위해 사용된 프로토콜
  * `url`: 리디렉션을 따라 최종적으로 요청된 URL
  * `status`: 성공, 실패 등을 나타내는 응답의 상태 코드
  * `message`: 응답의 성격을 설명하는 텍스트 메시지
  * `headers`: 응답과 함께 반환된 모든 헤더

이 응답 중 일부의 의미와 가용성은 요청에 사용된 프로토콜에 따라 다릅니다. HTTP/S 및 S/FTP를 포함한 많은 프로토콜에서 2xx 상태 코드는 성공적인 응답을 나타냅니다. 헤더를 지원하지 않는 프로토콜의 응답에서는 헤더 벡터가 비어 있습니다. HTTP/2는 상태 메시지를 포함하지 않고 상태 코드만 포함하므로 메시지는 비어 있습니다.
