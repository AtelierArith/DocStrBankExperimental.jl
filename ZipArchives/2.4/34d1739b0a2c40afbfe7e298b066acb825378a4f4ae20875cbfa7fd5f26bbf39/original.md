```
zip_crc32(data::AbstractVector{UInt8}, crc::UInt32=UInt32(0))::UInt32
```

Return the standard zip CRC32 checksum of data

See also [`zip_stored_crc32`](@ref), [`zip_test_entry`](@ref).
