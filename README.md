# mac disk uasge

find disk usage and free space for import stuff

## 0、常规检查

- [How to Clear the System and Internet Caches on a Mac](https://www.makeuseof.com/tag/clear-cache-mac/)
	- 使用[OnyX](https://www.titanium-software.fr/en/onyx.html)清理，可获得数十GB空间
- 检查清理[Docker](https://docs.docker.com/engine/reference/commandline/system_prune/)占用空间

```
# df Show docker disk usage
$ docker system df

# --all Remove all unused images not just dangling ones
# --volumes Prune volumes
$ docker system prune --all --volumes
```

## 1、查询方法

```
du -shc ./* | sort -hr
```

### 1.1、检查点

**1.1.1、主检查点**

```
~
~/Library/Caches
~/Library/Caches/com.apple.dt.Xcode/Downloads/
~/Library/Application Support
~/Desktop
/Applications
```

**1.1.2、XCode相关**

```
~/Library/Developer/CoreSimulator/Devices
~/Library/Developer/Xcode/DerivedData
~/Library/Developer/Xcode/Archives
~/Library/Developer/Xcode/UserData
~/Library/Developer/Xcode/UserData/IB\ Support/Simulator\ Devices
```

**1.1.3、CocoaPods相关**

```
~/.cocoapods/repos/
```

**1.1.4、Homebrew相关**

```
$ brew --cache
~/Library/Caches/Homebrew
```

**1.1.5、Android相关**

```
~/Library/Caches/AndroidStudio3.3
```

**1.1.6、AppStore应用程序沙盒目录**

```
~/Library/Group Containers
~/Library/Group Containers/UBF8T346G9.Office/Outlook/Outlook 15 Profiles/Main Profile/Data
```

### 1.2、检查命令

**1.2.1、查询目录{DIR}下文件大小**

```
du -shc {DIR}/* | sort -hr
```

**1.2.2、查询当前目录下文件大小**

```
du -shc ./* | sort -hr
```

## 2、命令行基础

### 2.1、du

```
-c        Display a grand total.
-d depth  Display an entry for all files and directories depth directories deep.
-s        Display an entry for each specified file.  (Equivalent to -d 0)
-h        "Human-readable" output.  Use unit suffixes: Byte, Kilobyte, Megabyte, Gigabyte, Terabyte and Petabyte.
```

### 2.2、sort

```
-h, --human-numeric-sort, --sort=human-numeric
-r, --reverse
```

### 2.3、组合使用


**2.3.1、查询某文件夹大小**

```
du -sh ~/Library/Caches
```

示例输出

```
$ du -sh ~/Library/Caches
13G	~/Library/Caches
```

**2.3.2、查询文件夹下详情**

```
du -shc ~/Library/Caches/* | sort -hr
```

示例输出

```
$ du -shc ~/Library/Caches/* | sort -hr
 13G	total
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