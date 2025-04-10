```
x::EscapeInfo
```

エスケープ情報のためのラティスで、以下のプロパティを保持します：

  * `x.Analyzed::Bool`: ラティスの正式な部分ではなく、`x` が分析されたかどうかを示します
  * `x.ReturnEscape::Bool`: `x` が戻り値を介して呼び出し元にエスケープできることを示します
  * `x.ThrownEscape::BitSet`: `x` が例外としてスローされる可能性のあるSSAステートメント番号を記録します：

      * `isempty(x.ThrownEscape)`: `x` はこのコールフレームで決してスローされません（ボトム）
      * `pc ∈ x.ThrownEscape`: `x` は `pc` のSSAステートメントでスローされる可能性があります
      * `-1 ∈ x.ThrownEscape`: `x` はこのコールフレームの任意のポイントでスローされる可能性があります（トップ）

    この情報は、`escape_exception!` によって例外を介して潜在的なエスケープを伝播するために使用されます。
  * `x.AliasInfo::Union{Bool,IndexableFields,IndexableElements,Unindexable}`: `x` のフィールドまたは配列要素にエイリアスされる可能性のあるすべての値を保持します：

      * `x.AliasInfo === false` は、`x` のフィールド/要素がまだ分析されていないことを示します
      * `x.AliasInfo === true` は、`x` のフィールド/要素が分析できないことを示します。例えば、`x` の型が不明であるか、具体的でないため、そのフィールド/要素を正確に知ることができません
      * `x.AliasInfo::IndexableFields` は、オブジェクト `x` のフィールドにエイリアスされる可能性のあるすべての値を正確なインデックス情報と共に記録します
      * `x.AliasInfo::IndexableElements` は、配列 `x` の要素にエイリアスされる可能性のあるすべての値を正確なインデックス情報と共に記録します
      * `x.AliasInfo::Unindexable` は、正確なインデックス情報なしに `x` のフィールド/要素にエイリアスされる可能性のあるすべての値を記録します
  * `x.Liveness::BitSet`: `x` が生きているべきSSAステートメント番号を記録します。例えば、呼び出し引数として使用される、呼び出し元に返される、または `:foreigncall` のために保持されるべきです：

      * `isempty(x.Liveness)`: `x` はこのコールフレームで決して使用されません（ボトム）
      * `0 ∈ x.Liveness` は、現在分析中のコールフレームの呼び出し引数であることを示す特別な意味を持ちます（したがって、呼び出し元からすぐに見える）。
      * `pc ∈ x.Liveness`: `x` は `pc` のSSAステートメントで使用される可能性があります
      * `-1 ∈ x.Liveness`: `x` はこのコールフレームの任意のポイントで使用される可能性があります（トップ）

一般的な `EscapeInfo` を作成するためのユーティリティコンストラクタがあります。例えば、

  * `NoEscape()`: このラティスのボトム（類似）要素で、どこにもエスケープしないことを意味します
  * `AllEscape()`: このラティスの最上位要素で、どこにでもエスケープすることを意味します

`analyze_escapes` は、これらの要素をボトムからトップに遷移させます。これは、Julia のネイティブ型推論ルーチンと同じ方向です。抽象状態はボトム（類似）要素で初期化されます：

  * 呼び出し引数は `ArgEscape()` として初期化され、その `Liveness` プロパティには `0` が含まれ、呼び出し引数として渡され、呼び出し元からすぐに見えることを示します
  * 他の状態は `NotAnalyzed()` として初期化されます。これは `NoEscape` よりもわずかに低い特別なラティス要素ですが、同時にまだ分析されていないこと以外の意味を持ちません（したがって、正式にはラティスの一部ではありません）
