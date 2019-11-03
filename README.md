# mac_disk_uasge
find disk usage and free space for import stuff

## 1 查询方法

### 1.1 检查点

```
~
~/Library/Caches
~/Desktop
```

### 1.2 检查命令

```
du -sh {DIR}/* | sort -hr
```

## 2 命令行基础

### 2.1 sort

```
-h, --human-numeric-sort, --sort=human-numeric
-r, --reverse
```

### 2.2 du

```
-s      Display an entry for each specified file.  (Equivalent to -d 0)
-d depth
        Display an entry for all files and directories depth directories deep.
-h      "Human-readable" output.  Use unit suffixes: Byte, Kilobyte, Megabyte, Gigabyte, Terabyte and Petabyte.
```

### 2.3 组合使用

```
du -sh ~/Library/Caches/* | sort -hr
```

示例输出

```
$ du -sh ~/Library/Caches/* | sort -hr
4.5G	~/Library/Caches/com.apple.dt.Xcode
1.0G	~/Library/Caches/Yarn
879M	~/Library/Caches/AndroidStudio3.3
652M	~/Library/Caches/com.apple.helpd
120M	~/Library/Caches/Homebrew
1.1M	~/Library/Caches/com.apple.AddressBookSourceSync
1.0M	~/Library/Caches/storedownloadd
808K	~/Library/Caches/knowledge-agent
644K	~/Library/Caches/com.apple.iBooksX
```