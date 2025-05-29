```
zip_crc32(data::AbstractVector{UInt8}, crc::UInt32=UInt32(0))::UInt32
```

データの標準的なzip CRC32チェックサムを返します

関連情報としては [`zip_stored_crc32`](@ref)、[`zip_test_entry`](@ref) を参照してください。
