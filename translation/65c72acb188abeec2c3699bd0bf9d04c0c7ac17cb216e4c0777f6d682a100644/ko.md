"     get*test*counts(::AbstractTestSet) -> TestCounts

테스트 세트에서 각 유형의 테스트 결과 수를 직접 계산하고 자식 테스트 세트에서 총계를 계산하는 재귀 함수입니다.

사용자 정의 `AbstractTestSet`은 이 함수를 구현하여 `DefaultTestSet`과 함께 총계를 계산하고 표시해야 합니다.

사용자 정의 `TestSet`에 대해 이 기능이 구현되지 않은 경우, 출력은 실패에 대해 `x`를 보고하고 지속 시간에 대해 `?s`로 대체됩니다.
