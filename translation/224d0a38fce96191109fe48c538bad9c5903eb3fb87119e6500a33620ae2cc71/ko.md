```
merge_analysis(repo::GitRepo, anns::Vector{GitAnnotated}) -> analysis, preference
```

주석이 달린 브랜치 팁 `anns`가 가리키는 브랜치에서 분석을 실행하고, 어떤 상황에서 병합이 가능한지 결정합니다. 예를 들어, `anns[1]`이 단순히 `anns[2]`의 조상인 경우, `merge_analysis`는 패스트 포워드 병합이 가능하다고 보고할 것입니다.

두 개의 출력을 반환합니다: `analysis`와 `preference`. `analysis`는 여러 가능한 값을 가집니다: 

  * `MERGE_ANALYSIS_NONE`: `anns`의 요소를 병합할 수 없습니다.
  * `MERGE_ANALYSIS_NORMAL`: HEAD와 사용자가 병합하고자 하는 커밋이 모두 공통 조상에서 분기된 경우의 일반적인 병합입니다. 이 경우 변경 사항을 해결해야 하며 충돌이 발생할 수 있습니다.
  * `MERGE_ANALYSIS_UP_TO_DATE`: 사용자가 병합하고자 하는 모든 입력 커밋이 HEAD에서 도달할 수 있으므로 병합을 수행할 필요가 없습니다.
  * `MERGE_ANALYSIS_FASTFORWARD`: 입력 커밋이 HEAD의 자손이므로 병합을 수행할 필요가 없습니다 - 대신 사용자는 단순히 입력 커밋을 체크아웃할 수 있습니다.
  * `MERGE_ANALYSIS_UNBORN`: 리포지토리의 HEAD가 존재하지 않는 커밋을 가리킵니다. 병합할 수는 없지만 입력 커밋을 체크아웃할 수 있을 수 있습니다.

`preference`도 여러 가능한 값을 가집니다: 

  * `MERGE_PREFERENCE_NONE`: 사용자가 선호도가 없습니다.
  * `MERGE_PREFERENCE_NO_FASTFORWARD`: 패스트 포워드 병합을 허용하지 않습니다.
  * `MERGE_PREFERENCE_FASTFORWARD_ONLY`: 패스트 포워드 병합만 허용하고 다른 유형(충돌을 초래할 수 있음)은 허용하지 않습니다. `preference`는 리포지토리 또는 전역 git 구성에 따라 제어할 수 있습니다.
