```
crystal = Crystal(filename;
    check_neutrality=true, net_charge_tol=1e-4,
    check_overlap=true, convert_to_p1=true,
    read_bonds_from_file=false, wrap_coords=true,
    include_zero_charges=true,
    remove_duplicates=false,
    species_col=["_atom_site_type_symbol", "_atom_site_label"]
    ) # read from file

crystal = Crystal(name, box, atoms, charges) # construct from matter, no bonds, P1-symmetry assumed
```

結晶構造ファイル（.cifまたは.cssr）を読み込み、`Crystal`データ構造を populated するか、`Crystal`データ構造を直接構築します。

# 引数

  * `filename::AbstractString`: 結晶構造ファイルの名前（`.cif`または`.cssr`を含む）で、`PATH_TO_CRYSTALS`から読み取ります。
  * `check_neutrality::Bool`: 電荷の中立性をチェックするかどうか
  * `net_charge_tol::Float64`: 電荷の中立性をチェックする際、ネット電荷の絶対値がこの値より大きい場合にエラーをスローします。
  * `check_overlap::Bool`: 重なり合う原子が検出された場合にエラーをスローします。
  * `convert_to_p1::Bool`: 構造がP1でない場合、.cifファイルの`_symmetry_equiv_pos_as_xyz`リストの対称性ルールを使用してP1対称性に変換されます。（対称性ルールを調べるために空間群名は使用しません）。
  * `read_bonds_from_file::Bool`: cifファイルから結合情報を読み取るかどうか。falseの場合、結合は後で推測できます。注意：結晶がP1対称性でない場合、結合を読み取ることとP1対称性に変換することは同時にできません。
  * `wrap_coords::Bool`: `true`の場合、原子と電荷の分数座標が[0,1]³に収まるようにmod(x, 1)を強制します。
  * `include_zero_charges::Bool`: `false`の場合、電荷がゼロの原子を`crystal.charges`に含めず、静電計算を高速化します。`true`の場合、ゼロ電荷の原子を`crystal.charges`に含め、原子の数が電荷の数と等しく、`crystal.charges.coords.xf`と`crystal.atoms.coords.xf`が同じであることを保証します。
  * `remove_duplicates::Bool`: 重複する原子と電荷を削除します。原子は同じ種である場合のみ重複と見なされます。
  * `species_col::Array{String}`: `crystal.atoms.species`の種の識別に使用する列。優先リストを使用します：.cifファイル内の`species_col`の最初のエントリをチェックし、存在しない場合は次のエントリを使用します。
  * `infer_bonds::Bool`: trueの場合、結合が自動的に推測されます。設定された場合、`periodic_boundaries`を指定する必要があります。デフォルトでは、結合は推測されません。
  * `periodic_boundaries::Union{Bool, Missing}`: `infer_bonds`と共に使用して、単位セル境界の取り扱いを指定します。単位セルのエッジを周期的境界として扱うには`true`を設定し（結合を許可）、ローカル単位セル内の結合に制限するには`false`を設定します。デフォルトでは、結合は推測されません。
  * `absolute_path::Bool`: デフォルトのパスではなく、絶対パスから読み込むには`true`を設定します。

# 戻り値

  * `crystal::Crystal`: 結晶構造情報を含む結晶

# 属性

  * `name::AbstractString`: 結晶構造の名前
  * `box::Box`: 単位セル（ブラヴァイス格子）
  * `atoms::Atoms`: 結晶単位セル内の原子のリスト
  * `charges::Charges`: 結晶単位セル内の点電荷のリスト
  * `bonds::MetaGraph`: 結晶内で結合されているすべての原子を示す非加重無向グラフ
  * `symmetry::SymmetryInfo`: 対称性情報
