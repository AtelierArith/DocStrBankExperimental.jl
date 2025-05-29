```
is_valid!([sink::IO,] zf::ZipFileSource) -> Bool
```

Validate that the contents read from an archived file match the information stored in the Local File Header, optionally writing remaining file information to a sink.

If the contents of the file do not match the information in the Local File Header, the method will describe the detected error using `@error` logging. The method checks that the compressed and uncompressed file sizes match what is in the header and that the CRC-32 of the uncompressed data matches what is reported in the header. Validation will work even on files that have been partially read.

The exclaimation mark in the function name is a warning to the user that the function destructively reads bytes from the `ZipFileSource`. If `sink` is provided, the remaining unread bytes from `zf` will be extracted into `sink`.

Because data cannot be written to a `ZipFileSource`, repeated calls to `is_valid!` will return the same result each time, but will only extract data to `sink` on the first call.
