```
stat(file)
```

返回一个结构体，其字段包含有关文件的信息。结构体的字段如下：

| 名称      | 类型                              | 描述                    |
|:------- |:------------------------------- |:--------------------- |
| desc    | `Union{String, Base.OS_HANDLE}` | 文件的路径或操作系统文件描述符       |
| size    | `Int64`                         | 文件的大小（以字节为单位）         |
| device  | `UInt`                          | 包含该文件的设备的ID           |
| inode   | `UInt`                          | 文件的inode号             |
| mode    | `UInt`                          | 文件的保护模式               |
| nlink   | `Int`                           | 指向该文件的硬链接数量           |
| uid     | `UInt`                          | 文件所有者的用户ID            |
| gid     | `UInt`                          | 文件所有者的组ID             |
| rdev    | `UInt`                          | 如果该文件指向一个设备，则指向该设备的ID |
| blksize | `Int64`                         | 文件系统为该文件首选的块大小        |
| blocks  | `Int64`                         | 分配的512字节块的数量          |
| mtime   | `Float64`                       | 文件最后修改的Unix时间戳        |
| ctime   | `Float64`                       | 文件元数据更改的Unix时间戳       |
