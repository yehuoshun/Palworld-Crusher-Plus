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

### 新增（不覆盖原版）

| 原料 | 产物 | 比例 |
|------|------|------|
| 石头 | 矿石 | 10:1 |
| 石头 | 煤炭 | 20:1 |
| 木头 | 木炭 | 5:1 |
| 木头 | 纤维 | 3:1 |

## 技术细节

- 数据表：`DT_ItemRecipeDataTable_Common`（参考 True Recipes 确认）
- 字段参考 PalSchema 官方 schema 定义