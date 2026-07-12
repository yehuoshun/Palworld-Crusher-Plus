# 测试清单

---

## 1. 装前置环境

### 1.1 装 UE4SS

1. 打开 https://github.com/Okaetsu/RE-UE4SS/releases/tag/experimental-palworld
2. 下载 `UE4SS_v3.0.1.zip`（或最新版）
3. 解压到游戏目录：`Palworld\Pal\Binaries\Win64\`
4. 解压后应该能看到 `ue4ss` 文件夹、`dwmapi.dll`、`xinput1_3.dll` 等文件
5. 打开 `ue4ss\UE4SS-settings.ini`，找到 `[Debug]` 部分，把这两行改成 1：
   ```ini
   GuiConsoleEnabled = 1
   GuiConsoleVisible = 1
   ```
   （这两个开了才能看到 PalSchema 的控制台输出，测完记得关掉，影响性能）

### 1.2 装 PalSchema

1. 打开 https://github.com/Okaetsu/PalSchema/releases
2. 下载最新版 `PalSchema_x.x.x.zip`（不要下 Dev 版，那个是给开发者用的）
3. 解压到 `Palworld\Pal\Binaries\Win64\ue4ss\Mods\`
4. 解压后路径应该是：`ue4ss\Mods\PalSchema\`（里面有 `dlls`、`config`、`mods`、`schemas` 等文件夹）

### 1.3 装本 Mod

1. 从仓库下载 `CrusherPlus` 文件夹
2. 复制到 `Palworld\Pal\Binaries\Win64\ue4ss\Mods\PalSchema\mods\`
3. 最终路径：`ue4ss\Mods\PalSchema\mods\CrusherPlus\raw\crusher_recipes.json`

---

## 2. 用 FModel 查表名和字段名

### 2.1 安装 FModel

1. 下载 FModel：https://fmodel.app/
2. 安装后打开，首次运行需要选游戏：
   - 点 `Add Undetected Game`
   - Directory 选 `Palworld\Pal\Content\Paks\`
   - 点 `+` 添加
3. 左侧选 `Palworld`，双击打开

### 2.2 找到粉碎机配方表

1. 在 FModel 左侧目录树里展开：
   ```
   Pal/Content/Pal/DataTable/
   ```
2. 在搜索框输入 `Convert`，看有没有 `DT_ItemConvertDataTable` 或类似名字
3. 如果 `Convert` 搜不到，搜 `Crusher`
4. 找到后**右键 → Extract** 导出为 JSON，看看里面数据结构

### 2.3 确认字段名

打开导出的 JSON，看每一行的结构。举例（推测）：
```json
{
  "RowName": "Crusher_StoneToPaldium",
  "ProductItemId": "Pal_crystal_S",
  "ProductCount": 1,
  "WorkAmount": 50.0,
  "Material1_ItemId": "Stone",
  "Material1_Count": 5
}
```

**把实际看到的字段名记下来，和 mod 里用的对比：**
- 产物 ID → 我写的 `ProductItemId`，实际是？
- 产物数量 → 我写的 `ProductCount`，实际是？
- 工作量 → 我写的 `WorkAmount`，实际是？
- 原料 ID → 我写的 `Material1_ItemId`，实际是？
- 原料数量 → 我写的 `Material1_Count`，实际是？

如果有 `Material2_ItemId` 之类的，说明支持多种原料，也记下来。

---

## 3. 启动游戏测试

### 3.1 看 UE4SS 控制台

1. 启动 Palworld
2. 游戏加载时，UE4SS 会弹出一个黑色的控制台窗口
3. 切到 **Pal Schema** 标签页
4. 看有没有**红色**的报错信息，常见报错：
   - `Table not found: DT_xxx` → 表名不对
   - `Invalid property: xxx` → 字段名不对
   - `Failed to load mod: CrusherPlus` → 路径或 JSON 格式有问题
5. **截图控制台，不管有没有报错都截**

### 3.2 进游戏验证

1. 进存档，造一个粉碎机（或者用已有的）
2. 打开粉碎机界面
3. 看配方列表里有没有新增的四个配方
4. 放石头进去，看能不能选「矿石」或「煤炭」
5. 放木头进去，看能不能选「木炭」或「纤维」
6. 确认能正常产出物品

---

## 4. 反馈格式

把以下内容发我：

```
表名：____________________

字段名对照（我写的 → 实际的）：
  ProductItemId  → _________
  ProductCount   → _________
  WorkAmount     → _________
  Material1_ItemId → _________
  Material1_Count  → _________

UE4SS 控制台：
  [截图]

游戏内测试：
  [有没有看到新配方？能正常产出吗？]
```

---

## 附：常见问题

| 问题 | 可能原因 |
|------|---------|
| UE4SS 控制台不弹 | `GuiConsoleEnabled` 没设成 1 |
| 游戏闪退 | UE4SS 版本不对，用 Palworld 专用版 |
| PalSchema 标签页没有 | PalSchema 没装好，检查路径 |
| 粉碎机里没有新配方 | 表名或字段名不对 |
| 选了配方但不出东西 | 物品 ID 写错了 |