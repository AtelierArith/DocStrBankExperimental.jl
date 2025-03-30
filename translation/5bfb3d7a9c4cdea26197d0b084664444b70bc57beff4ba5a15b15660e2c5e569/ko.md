```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError`는 예외 객체로서 요청에 대한 실패한 응답의 속성을 캡처하는 타입입니다:

  * `url`: 리디렉션 없이 요청된 원래 URL
  * `code`: libcurl 오류 코드; 프로토콜 전용 오류가 발생한 경우 `0`
  * `message`: 무엇이 잘못되었는지를 나타내는 libcurl 오류 메시지
  * `response`: 사용 가능한 응답 정보를 캡처하는 응답 객체

같은 `RequestError` 타입은 요청이 성공했지만 2xx 범위에 없는 상태 코드로 표시된 프로토콜 수준 오류가 있는 경우 `download`에 의해 발생합니다. 이 경우 `code`는 제로가 되고 `message` 필드는 빈 문자열이 됩니다. `request` API는 libcurl 오류 `code`가 0이 아닐 때만 `RequestError`를 발생시키며, 이 경우 포함된 `response` 객체는 `status`가 0이고 메시지가 비어 있을 가능성이 높습니다. 그러나 프로토콜 오류로 인해 curl 수준 오류가 발생하는 상황도 있으며, 이 경우 내부 및 외부 코드와 메시지가 모두 관심의 대상이 될 수 있습니다.
