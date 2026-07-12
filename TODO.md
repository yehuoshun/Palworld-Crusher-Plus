# 测试清单

> 放弃 FModel 方案，改用 PalSchema + VSCode 自动补全找表名。

---

## 1. 装前置环境

### 1.1 装 UE4SS

1. 打开 https://github.com/Okaetsu/RE-UE4SS/releases/tag/experimental-palworld
2. 下载 `UE4SS_v3.0.1.zip`
3. 解压到 `Palworld\Pal\Binaries\Win64\`
4. 打开 `ue4ss\UE4SS-settings.ini`，`[Debug]` 部分改成：
   ```ini
   GuiConsoleEnabled = 1
   GuiConsoleVisible = 1
   ```

### 1.2 装 PalSchema

1. 打开 https://github.com/Okaetsu/PalSchema/releases
2. 下载 `PalSchema_0.6.0.zip`
3. 解压到 `Palworld\Pal\Binaries\Win64\ue4ss\Mods\`
4. 最终路径：`ue4ss\Mods\PalSchema\`（里面有 `dlls`、`mods`、`schemas` 等文件夹）

### 1.3 装 VSCode

1. 下载 https://code.visualstudio.com/
2. 安装时勾选「Add "Open with Code"」

---

## 2. 生成 Schema 文件

1. 启动 Palworld → UE4SS 控制台弹出
2. 切到 **Pal Schema** 标签页
3. 点 **Generate JSON Schema Files**，等进度条跑完
4. 关游戏

---

## 3. 找表名和字段名

1. 右键 `ue4ss\Mods\PalSchema` 文件夹 → **Open with Code**
2. 左侧目录树展开 `mods` 文件夹
3. 右键 `mods` → **New Folder** → 命名 `CrusherPlus`
4. 右键 `CrusherPlus` → **New Folder** → 命名 `raw`
5. 右键 `raw` → **New File** → 命名 `crusher_recipes.json`
6. 打开 `crusher_recipes.json`，输入 `{` 然后回车
7. 输入 `"DT_`（注意引号和下划线），VSCode 会自动列出所有 400+ 张数据表
8. 在列表里搜 `convert` 或 `product`，找到粉碎机配方表名
9. 选中表名后，继续输入 `"` → 回车，VSCode 会自动补全表内的字段名

**记下来：**
```
表名：____________________
字段名（按自动补全列表抄）：
```
把表名和字段名发我。

---

## 4. 装本 Mod

1. 把仓库里的 `CrusherPlus` 文件夹复制到 `ue4ss\Mods\PalSchema\mods\`
2. 最终路径：`ue4ss\Mods\PalSchema\mods\CrusherPlus\raw\crusher_recipes.json`

---

## 5. 启动测试

1. 启动 Palworld，看 UE4SS 控制台 Pal Schema 标签页有没有红字报错
2. 进游戏造粉碎机，看配方列表里有没有新配方
3. 丢石头/木头进去，确认能正常产出

---

## 如果还是不行

放弃 PalSchema 方案，换别的方式实现。