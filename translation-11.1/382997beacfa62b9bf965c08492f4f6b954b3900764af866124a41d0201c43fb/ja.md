```
Base.@assume_effects 設定... [ex]
```

コンパイラの効果モデリングをオーバーライドします。このマクロは、いくつかのコンテキストで使用できます。

1. メソッド定義の直前に、適用されたメソッドの全体的な効果モデリングをオーバーライドするために。
2. 引数なしの関数本体内で、囲むメソッドの全体的な効果モデリングをオーバーライドするために。
3. コードブロックに適用して、適用されたコードブロックのローカルな効果モデリングをオーバーライドするために。

# 例

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # 使用例 1:
           # この :terminates_locally により `fact` が定数折りたたみ可能になります
           res = 1
           0 ≤ x < 20 || error("bad fact")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (generic function with 1 method)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # 使用例 2:
               # この :terminates_locally によりこの無名関数が定数折りたたみ可能になります
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("bad fact")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("bad fact")
               # 使用例 3:
               # この :terminates_locally アノテーションによりコンパイラは汚染をスキップします
               # この `while` ブロック内の `:terminates` 効果を許可し、親
               # 無名関数が定数折りたたみ可能になります
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! compat "Julia 1.8"
    `Base.@assume_effects` を使用するには、Julia バージョン 1.8 が必要です。


!!! compat "Julia 1.10"
    関数本体内での使用には、少なくとも Julia 1.10 が必要です。


!!! compat "Julia 1.11"
    コードブロックのアノテーションには、少なくとも Julia 1.11 が必要です。


!!! warning
    このマクロの不適切な使用は未定義の動作を引き起こす可能性があります（クラッシュ、不正確な回答、または追跡が難しいバグを含む）。注意して使用し、絶対に必要な場合にのみ最後の手段として使用してください。そのような場合でも、効果の主張の強さを最小限に抑えるために可能な限りの手段を講じるべきです（例：`：nothrow` が十分であった場合は `:total` を使用しない）。


一般に、各 `setting` 値は、関数の動作に関する主張を行いますが、コンパイラにその動作が実際に真であることを証明させる必要はありません。これらの主張はすべてのワールドエイジに対して行われます。したがって、後で拡張されて仮定を無効にする可能性のある一般的な関数の使用を制限することが推奨されます（これにより未定義の動作が引き起こされる可能性があります）。

以下の `setting` がサポートされています。

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# 拡張ヘルプ

---

## `:consistent`

`:consistent` 設定は、等価 (`===`) 入力に対して次のことを主張します：

  * 終了の方法（戻り値、例外、非終了）は常に同じです。
  * メソッドが戻る場合、結果は常に等価です。

!!! note
    これは特に、メソッドが新しく割り当てられた可変オブジェクトを返さないことを意味します。可変オブジェクトの複数の割り当て（内容が同一であっても）は等価ではありません。


!!! note
    `:consistent`-cy の主張はワールドエイジごとに行われます。より正式には、$fᵢ$ をワールドエイジ $i$ における $f$ の評価と書くと、この設定は次のことを要求します：

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    ただし、2つのワールドエイジ $i$, $j$ について $i ≠ j$ の場合、$fᵢ(x) ≢ fⱼ(y)$ である可能性があります。

    さらに、`：consistent` 関数は、ヒープの状態や特定のワールドエイジに対して一定でない他のグローバル状態に依存して戻り値を決定してはなりません。


!!! note
    `:consistent`-cy には、オプティマイザによって行われるすべての合法的な書き換えが含まれます。たとえば、浮動小数点の fastmath 操作は `:consistent` と見なされません。なぜなら、オプティマイザがそれらを書き換える可能性があり、同じワールドエイジであっても出力が `:consistent` でなくなるからです（例：一方がインタプリタで実行され、もう一方が最適化された場合など）。


!!! note
    `:consistent` 関数が例外をスローして終了する場合、その例外自体は上記の等価性要件を満たす必要はありません。


---

## `:effect_free`

`:effect_free` 設定は、メソッドが外部的に意味的に可視な副作用がないことを主張します。以下は、外部的に意味的に可視な副作用の不完全なリストです：

  * グローバル変数の値を変更すること。
  * ヒープを変更すること（例：配列や可変値）、ただし以下に記載されている場合を除く。
  * メソッドテーブルを変更すること（例：eval への呼び出しを通じて）。
  * ファイル/ネットワーク/etc. I/O。
  * タスクの切り替え。

ただし、以下は明示的に意味的に可視ではありませんが、観察可能である場合があります：

  * メモリ割り当て（可変および不変の両方）。
  * 経過時間。
  * ガーベジコレクション。
  * メソッドのライフタイムを超えないオブジェクトのヒープの変更（すなわち、メソッド内で割り当てられ、エスケープしないもの）。
  * 戻り値（外部的に可視ですが、副作用ではありません）。

ここでのルールは、外部的に可視な副作用は、関数が実行されなかった場合にプログラムの残りの部分の実行に影響を与えるものです。

!!! note
    `:effect_free` の主張は、メソッド自体とメソッドによって実行されるコードの両方に対して行われます。この主張はすべてのワールドエイジに対して有効でなければならず、それに応じてこの主張の使用を制限する必要があります。


---

## `:nothrow`

`:nothrow` 設定は、このメソッドが例外をスローしないこと（すなわち、常に値を返すか、決して返さないこと）を主張します。

!!! note
    `:nothrow` アノテーションが付けられたメソッドが内部で例外処理を使用することは許可されますが、例外がメソッド自体から再スローされることはありません。


!!! note
    メソッドの実行が `MethodError` や類似の例外を引き起こす可能性がある場合、そのメソッドは `:nothrow` と見なされません。ただし、`StackOverflowError` や `InterruptException` のような環境依存のエラーはこの効果によってモデル化されないため、`StackOverflowError` を引き起こす可能性のあるメソッドは必ずしも `!:nothrow` である必要はありません（ただし、通常は `!:terminates` であるべきです）。


---

## `:terminates_globally`

`:terminates_globally` 設定は、このメソッドが最終的に終了すること（通常または異常に）を主張します。すなわち、無限ループに陥らないことを意味します。

!!! note
    この `:terminates_globally` の主張は、アノテーションされたメソッドによって呼び出される他のすべてのメソッドをカバーします。


!!! note
    コンパイラは、メソッドが比較的*迅速に*終了することを示す強い指標と見なします。したがって、技術的には終了するが実際には終了しないメソッドにこの設定をアノテートするのは良くありません。


---

## `:terminates_locally`

`:terminates_locally` 設定は `:terminates_globally` と似ていますが、アノテーションされたメソッド内の構文的制御フローにのみ適用されます。したがって、メソッドが他のメソッドを呼び出す場合に非終了の可能性を許可する、はるかに弱い（したがって安全な）主張です。

!!! note
    `:terminates_globally` は `:terminates_locally` を含意します。


---

## `:notaskstate`

`:notaskstate` 設定は、メソッドがローカルタスク状態（タスクローカルストレージ、RNG状態など）を使用または変更せず、したがってタスク間で安全に移動できることを主張します。

!!! note
    例外処理の実装は、タスクオブジェクトに保存された状態を使用します。ただし、この状態は現在 `:notaskstate` の範囲内とは見なされず、`:nothrow` 効果を使用して別々に追跡されます。


!!! note
    `:notaskstate` の主張は、*現在実行中のタスク* の状態に関するものです。現在実行中のタスクを考慮しない他の手段によって `Task` オブジェクトへの参照が取得された場合、`:notaskstate` 効果は汚染される必要はありません。これは、該当するタスクオブジェクトが現在実行中のタスクと `===` である場合でも当てはまります。


!!! note
    タスク状態へのアクセスは、通常、他の効果の汚染も引き起こします。たとえば、タスク状態が変更された場合は `:effect_free`（もしタスク状態が変更された場合）や `:consistent`（もしタスク状態が結果の計算に使用された場合）などです。特に、`:notaskstate` ではないが、`:effect_free` および `:consistent` であるコードは、デッドコード削除され、したがって `:total` に昇格される可能性があります。


---

## `:inaccessiblememonly`

`:inaccessiblememonly` 設定は、メソッドが外部からアクセス可能な可変メモリにアクセスまたは変更しないことを主張します。これは、メソッドが他のメソッドやトップレベルの実行から戻る前にアクセスできない新しく割り当てられたオブジェクトの可変メモリにアクセスまたは変更できることを意味しますが、引数によって指される可変グローバル状態やメモリにはアクセスまたは変更できません。

!!! note
    以下は、この仮定を無効にする不完全なリストの例です：

      * 可変グローバル変数にアクセスするためのグローバル参照または `getglobal` 呼び出し
      * 非定数のグローバル変数に代入を行うためのグローバル代入または `setglobal!` 呼び出し
      * グローバル可変変数のフィールドを変更する `setfield!` 呼び出し


!!! note
    この `:inaccessiblememonly` の主張は、アノテーションされたメソッドによって呼び出される他のすべてのメソッドをカバーします。


---

## `:noub`

`:noub` 設定は、メソッドが未定義の動作を実行しないことを主張します（任意の入力に対して）。未定義の動作は、技術的には他の効果の主張（たとえば `:consistent` や `:effect_free`）を違反させる可能性がありますが、これをモデル化することはなく、未定義の動作が存在しないことを前提としています。

---

## `:nortcall`

`:nortcall` 設定は、メソッドが `Core.Compiler.return_type` を呼び出さず、このメソッドが呼び出す可能性のある他のメソッドも `Core.Compiler.return_type` を呼び出さないことを主張します。

!!! note
    正確には、この主張は、`Core.Compiler.return_type` への呼び出しが実行時に行われない場合に使用できます。すなわち、`Core.Compiler.return_type` の結果がコンパイル時に正確に知られており、呼び出しがオプティマイザによって排除される場合です。ただし、`Core.Compiler.return_type` の結果がコンパイル時に折りたたまれるかどうかは、コンパイラの実装に大きく依存するため、問題のメソッドが `Core.Compiler.return_type` を何らかの形で使用している場合、これを主張するのは一般的にリスクがあります。


---

## `:foldable`

この設定は、コンパイラがコンパイル時に呼び出しを定数折りたたみすることを保証するために必要な効果のセットの便利なショートカットです。現在、次の `setting` と同等です：

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! note
    このリストには特に `:nothrow` は含まれていません。コンパイラは、定数伝播を試み、コンパイル時にスローされたエラーを記録します。ただし、`:consistent`-cy の要件により、そのようにアノテートされた呼び出しは、同じ引数値に対して一貫してスローされる必要があります。


!!! note
    関数内の明示的な `@inbounds` アノテーションも定数折りたたみを無効にし、`:foldable` によって上書きされることはありません。


---

## `:removable`

この設定は、コンパイラがコンパイル時に未使用の結果を持つ呼び出しを削除することを保証するために必要な効果のセットの便利なショートカットです。現在、次の `setting` と同等です：

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

この `setting` は、可能な最大の効果のセットです。現在、次の他の `setting` を含意します：

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! warning
    `:total` は非常に強い主張であり、将来の Julia のバージョンで追加の意味を持つ可能性があります（たとえば、追加の効果が追加され、`:total` の定義に含まれる場合）。その結果、注意して使用する必要があります。可能な限り、特定のアプリケーションに必要な最小限の特定の効果の主張を使用することをお勧めします。多くの効果のオーバーライドが一連の関数に適用される場合、`:total` の使用よりもカスタムマクロを使用することが推奨されます。


---

## 否定された効果

効果名は `!` で接頭辞を付けることができ、効果が以前のメタ効果から削除されるべきことを示します。たとえば、`:total !:nothrow` は、呼び出しが一般的には全体的であるが、スローする可能性があることを示します。 ```
