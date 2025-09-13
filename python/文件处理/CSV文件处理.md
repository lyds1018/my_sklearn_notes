# 📂 Python 处理 CSV 文件常用语法

## 1. 使用内置 `csv` 模块

### (1) 读取 CSV

```
import csv

# 普通读取
with open("data.csv", "r", encoding="utf-8") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)   # row 是列表
```

带表头的 CSV，可以用 `DictReader`：

```
with open("data.csv", "r", encoding="utf-8") as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row["name"], row["age"])   # row 是字典
```

------

### (2) 写入 CSV

```
import csv

# 写入行列表
with open("data.csv", "w", encoding="utf-8", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["name", "age", "city"])
    writer.writerow(["Tom", 18, "Beijing"])
    writer.writerows([["Alice", 20, "Shanghai"], ["Bob", 22, "Shenzhen"]])
```

字典写入：

```
with open("data.csv", "w", encoding="utf-8", newline="") as f:
    fieldnames = ["name", "age"]
    writer = csv.DictWriter(f, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerow({"name": "Tom", "age": 18})
    writer.writerow({"name": "Alice", "age": 20})
```

------

## 2. 使用 `pandas`（更强大）

### (1) 读取 CSV

```
import pandas as pd

df = pd.read_csv("data.csv")
print(df.head())          # 查看前几行
print(df["name"])         # 读取某一列
```

常用参数：

```
df = pd.read_csv("data.csv", encoding="utf-8", sep=",", header=0)
sep：字段分隔符
header：列名所在行
```

------

### (2) 写入 CSV

```
df.to_csv("output.csv", index=False, encoding="utf-8")
```

------

### (3) 常用操作

```
# 筛选
print(df[df["age"] > 18])

# 添加新列
df["score"] = [90, 85, 88]

# 遍历
for i, row in df.iterrows():
    print(row["name"], row["age"])

# 基本统计
print(df.describe())
```

------

## 3. 大文件处理

逐行读取，避免内存占用过大：

```
import pandas as pd

for chunk in pd.read_csv("big.csv", chunksize=10000):
    print(chunk.head())
```