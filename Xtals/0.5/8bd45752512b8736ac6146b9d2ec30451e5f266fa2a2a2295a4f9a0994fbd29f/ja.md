```
simulation_ready_crystal = apply_symmetry_operations(non_p1_crystal)
```

内部対称性ルールに基づいて結晶をP1対称性に変換します。これにより、新しい結晶が返されます。

# 引数

  * `non_p1_crystal::Crystal`: P1対称性に変換される結晶

# 戻り値

  * `P1_crystal::Crystal`: P1対称性に変換された後の結晶。新しい対称性ルールはP1対称性ルールになります。
