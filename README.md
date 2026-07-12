# Palworld Crusher Plus

粉碎机配方扩展 Mod，基于 PalSchema，为 Palworld 粉碎机添加更多物品转换配方。

## 前置要求

- [UE4SS (Palworld 版)](https://github.com/Okaetsu/RE-UE4SS/releases/tag/experimental-palworld)
- [PalSchema](https://github.com/Okaetsu/PalSchema/releases)

## 安装

1. 安装 UE4SS → 解压到 `Palworld\Pal\Binaries\Win64\`
2. 安装 PalSchema → 解压到 `ue4ss\Mods\`
3. 将 `CrusherPlus` 文件夹复制到 `ue4ss\Mods\PalSchema\mods\`

最终路径：`Palworld\Pal\Binaries\Win64\ue4ss\Mods\PalSchema\mods\CrusherPlus\`

## 配方

| 原料 | 产物 | 比例 | 耗时 |
|------|------|------|------|
| 石头 | 金属矿石 | 10:1 | 1000 |
| 石头 | 石炭 | 20:1 | 1500 |
| 木头 | 木炭 | 5:1 | 500 |
| 木头 | 纤维 | 3:1 | 300 |
| 木头 | 木板 | 5:1 | 500 |
| 木头 | 优质木板 | 10:1 | 1000 |
| 纤维 | 布 | 3:1 | 500 |
| 纤维 | 优质布 | 10:1 | 1500 |
| 纤维 | 美丽花朵 | 5:1 | 500 |
| 纤维 | 皮革 | 10:1 | 1000 |

## 技术细节

- 数据表：`DT_ItemRecipeDataTable`（参考 True Recipes）
- 格式完全对齐 True Recipes，18 字段全齐
- 字段参考 PalSchema 官方 schema 定义
