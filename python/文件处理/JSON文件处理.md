# 📂 Python 处理 JSON 文件常用语法

## 1. 导入模块

```
import json
```

------

## 2. Python ↔ JSON 的区别

| Python    | JSON   |
| --------- | ------ |
| dict      | object |
| list      | array  |
| str       | string |
| int/float | number |
| True      | true   |
| False     | false  |
| None      | null   |

------

## 3. Python → JSON（序列化）

### 转换为 JSON 字符串

```
data = {"name": "Tom", "age": 18, "city": "Beijing"}
json_str = json.dumps(data, ensure_ascii=False, indent=2)
print(json_str)
```

- `ensure_ascii=False` → 保证中文正常显示
- `indent=2` → 格式化缩进

### 保存到文件

```
with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)
```

------

## 4. JSON → Python（反序列化）

### 从字符串解析

```
json_str = '{"name": "Tom", "age": 18}'
data = json.loads(json_str)
print(data["name"])   # Tom
```

### 从文件读取

```
with open("data.json", "r", encoding="utf-8") as f:
    data = json.load(f)
    print(data["age"])
```

------

## 5. 修改 JSON 数据

```
with open("data.json", "r", encoding="utf-8") as f:
    data = json.load(f)

data["age"] = 20
data["score"] = 95

with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)
```

------

## 6. 合并多个JSON

```
# 读取第一个 JSON 文件
with open('file1.json', 'r', encoding='utf-8') as f1:
    data1 = json.load(f1)

# 读取第二个 JSON 文件
with open('file2.json', 'r', encoding='utf-8') as f2:
    data2 = json.load(f2)

# 合并两个 JSON 数据
merged_data = [data1, data2]

# 将合并后的数据写入新的 JSON 文件
with open('merged_file.json', 'w', encoding='utf-8') as f_out:
    json.dump(merged_data, f_out, ensure_ascii=False, indent=2)
```