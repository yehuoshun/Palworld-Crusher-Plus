# 测试清单

## 1. 装前置

- [ ] 下载 [UE4SS Palworld 版](https://github.com/Okaetsu/RE-UE4SS/releases/tag/experimental-palworld)，解压到 `Palworld\Pal\Binaries\Win64\`
- [ ] 下载 [PalSchema](https://github.com/Okaetsu/PalSchema/releases)（选 `PalSchema_x.x.x.zip`），解压到 `ue4ss\Mods\`
- [ ] 将本仓库 `CrusherPlus` 文件夹复制到 `ue4ss\Mods\PalSchema\mods\`

## 2. 验证表名

- [ ] 下载 [FModel](https://fmodel.app/)，打开 Palworld 的 pak 文件
- [ ] 找到 `Pal/Content/Pal/DataTable/` 目录
- [ ] 搜索 `Convert` 或 `Crusher`，找到粉碎机配方表的确切文件名
- [ ] 如果表名不是 `DT_ItemConvertDataTable`，修改 `crusher_recipes.json` 里的表名

## 3. 验证字段名

- [ ] 用 FModel 点开粉碎机配方表，看每列的字段名
- [ ] 当前用的字段名（可能需要调整）：
  - `ProductItemId` — 产物物品 ID
  - `ProductCount` — 产物数量
  - `WorkAmount` — 所需工作量
  - `Material1_ItemId` — 原料物品 ID
  - `Material1_Count` — 原料数量
- [ ] 如果游戏里实际字段名不同，改 `crusher_recipes.json`

## 4. 启动测试

- [ ] 启动 Palworld，看 UE4SS 控制台有没有红字报错
- [ ] 进游戏，造粉碎机，看配方列表里有没有新配方
- [ ] 丢石头/木头进去，确认能产出对应物品

## 5. 反馈

把以下信息发我：
- 粉碎机配方表的**确切文件名**
- 表中每列的**字段名和类型**
- 游戏里有没有报错（截图 UE4SS 控制台）