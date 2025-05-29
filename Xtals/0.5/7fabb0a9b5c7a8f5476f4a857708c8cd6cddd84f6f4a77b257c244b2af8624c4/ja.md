```
atoms, bonds = read_mol("molecule.mol")
```

`.mol`ファイルを読み込み、原子と結合に関する情報を含みます。`.mol`ファイルの構造については[こちら](https://chem.libretexts.org/Courses/University_of_Arkansas_Little_Rock/ChemInformatics_(2017)%3A_Chem_4399%2F%2F5399/2.2%3A_Chemical_Representations_on_Computer%3A_Part_II/2.2.2%3A_Anatomy_of_a_MOL_file)を参照してください。

# 引数

  * `filename::AbstractString`: .molファイルのパスとファイル名（拡張子を含む必要があります）

# 戻り値

  * `atoms::Atoms{Cart}`: `.mol`ファイルから読み取った原子の集合。
  * `bonds::MetaGraph`: `.mol`ファイルから読み取った原子の結合グラフ。
  * `bond_types::Array{Int, 1}`: 結合タイプの配列。
