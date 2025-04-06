```
reject(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

향후 인증에서 재사용되지 않도록 `payload` 자격 증명을 폐기합니다. 인증이 실패했을 때만 호출해야 합니다.

`shred` 키워드는 페이로드 자격 증명 필드의 민감한 정보를 파괴할지 여부를 제어합니다. 테스트 중에는 `false`로 설정해야 합니다.
