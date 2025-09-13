# 📂 Python 处理 TXT 文件

## 1. 打开文件

```
# 语法: open(文件路径, 模式, 编码)
f = open("test.txt", "r", encoding="utf-8")
f.close()
```

| 模式   | 说明                                 |
| ------ | ------------------------------------ |
| `"r"`  | 读（默认，文件必须存在）             |
| `"w"`  | 写（覆盖原文件，不存在则新建）       |
| `"a"`  | 追加（在文件末尾写入，不存在则新建） |
| `"r+"` | 读写（文件必须存在）                 |
| `"b"`  | 二进制模式（如 `"rb"`、`"wb"`）      |

------

## 2. 读文件

```
# 推荐 with 自动关闭文件
with open("test.txt", "r", encoding="utf-8") as f:
    content = f.read()        # 一次性读所有内容
    print(content)

with open("test.txt", "r", encoding="utf-8") as f:
    line = f.readline()       # 读一行
    lines = f.readlines()     # 读所有行，返回列表
```

逐行读取（适合大文件）：

```
with open("big.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip())
```

------

## 3. 写文件

```
# 覆盖写
with open("test.txt", "w", encoding="utf-8") as f:
    f.write("Hello\n")
    f.write("World\n")

# 追加写
with open("test.txt", "a", encoding="utf-8") as f:
    f.write("追加内容\n")
```

------

## 4. 文件指针操作

```
with open("test.txt", "r", encoding="utf-8") as f:
    f.seek(0)         # 移动到开头
    print(f.read(5))  # 读前5个字符
    pos = f.tell()    # 获取当前位置
    print("位置:", pos)
```

------

## 5. 判断文件是否存在

```
import os

if os.path.exists("test.txt"):
    print("文件存在")
else:
    print("文件不存在")
```

------

## 6. 删除 / 重命名文件

```
import os

os.remove("test.txt")          # 删除文件
os.rename("old.txt", "new.txt")  # 重命名文件
```