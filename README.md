# EPMA 数据转换器

用于将 EPMA 数据导入 AX-Win 进行阳离子分析处理前的 Windows 格式转换器。

## 功能

- **Excel 转 TXT**：将 EPMA Excel 数据转换为适合导入 AX-Win 的文本格式。
- **TXT 转 Excel**：将 AX-Win 输出的 `tab.txt` 文件转换回 Excel 格式，便于后续整理和分析。
- 转换完成后可先预览结果，再选择保存。

## 下载

建议从仓库的 [Releases](https://github.com/Cchuan-hcr/Cchuan./releases/latest) 页面下载最新版本：

- `EPMA.exe`（页面显示标签为“EPMA 数据转换器（Windows）”）

当前版本：`v1.0.0`

GitHub 会自动简化 Release 附件中的中文文件名。Release 中的 `EPMA.exe` 与仓库内的 `EPMA数据转换.exe` 内容相同。

## 使用方法

1. 从 Releases 页面下载 `EPMA.exe`。
2. 双击运行程序。
3. 选择“Excel 转 TXT”或“TXT 转 Excel”，然后选择需要转换的文件。
4. 点击“转换”，检查预览内容无误后点击“保存”。

## Excel 转 TXT：输入格式要求

用于转换的 Excel 工作表必须按下面的结构填写，否则生成的 TXT 可能无法被 AX-Win/AX62 识别。

### 第 1 行：主量元素表头

第 1 行必须包含下面 11 个氧化物名称。为了让本转换器稳定识别，请严格使用示例中的名称和顺序，不要增加、删除或改写表头：

```text
SiO2    TiO2    Al2O3    Cr2O3    Fe2O3    FeO    MnO    MgO    CaO    Na2O    K2O
```

AX62 只接受这 11 种氧化物。每一行数据的数值顺序必须与第 1 行的表头顺序完全一致。
即使某种氧化物没有实测值，也必须保留对应列并填写 `0`，不能删除该列。

### 第 2 行：矿物代码和名称

- 在 `A2` 单元格中填写两个以空格分隔的单词，格式为：`矿物代码 自定义名称`。
- 第一个单词必须是下表列出的 AX62 矿物代码。
- 第二个单词可以自行命名，例如样品简称、分析组名或矿物简称；建议使用不含空格的简短名称。
- `B2:K2` 保持空白。

例如：

```text
fsp pl
```

其中 `fsp` 是长石类的矿物代码，`pl` 是自定义名称。

### 第 3 行及以后：EPMA 实测数据

- 从第 3 行开始填写 EPMA 实测主量元素数据。
- 每一行代表一个分析点，共填写 11 个数值。
- 不要在数据区域插入标题、注释、合并单元格或空白行。
- 同一工作表中的所有数据共用第 2 行填写的矿物代码和名称；不同矿物使用不同 Excel 文件最稳妥。如使用不同工作表，请在转换预览中逐项确认。
- 建议保留三位小数，零值直接填写为 `0` 或 `0.000`。

完整 Excel 结构示例：

```text
SiO2    TiO2    Al2O3    Cr2O3    Fe2O3    FeO     MnO     MgO     CaO      Na2O    K2O
fsp pl
45.051  0.030   34.377   0.000    0.000    0.695   0.000   0.289   18.213   0.755   0.015
45.517  0.024   33.497   0.000    0.000    1.007   0.000   0.331   18.266   0.793   0.017
```

转换器会为每一行实测数据重复写入第 2 行的矿物代码和名称，并在 TXT 文件末尾自动添加 `*`。上面的 Excel 示例将生成类似下面的内容：

```text
SiO2    TiO2    Al2O3    Cr2O3    Fe2O3    FeO     MnO     MgO     CaO      Na2O    K2O
fsp pl
45.051  0.030   34.377   0.000    0.000    0.695   0.000   0.289   18.213   0.755   0.015
fsp pl
45.517  0.024   33.497   0.000    0.000    1.007   0.000   0.331   18.266   0.793   0.017
*
```

程序实际使用制表符分隔各列；README 中以对齐空格展示是为了便于阅读。

### AX62 矿物代码

以下代码来自 `axNotes.pdf` 第 4 页的 “Mineral code abbreviations”：

| 代码 | Mineral groups（PDF 原文） |
| --- | --- |
| `mu` | white micas, including margarite |
| `bi` | biotites |
| `amph` | amphiboles |
| `fsp` | feldspars |
| `ep` | epidotes, zoisites |
| `g` | garnets |
| `cpx` | clinopyroxenes |
| `opx` | orthopyroxenes |
| `chl` | chlorites |
| `ta` | talc |
| `scap` | scapolites |
| `ol` | olivines |
| `ctd` | chloritoid |
| `cd` | cordierite |
| `st` | staurolites |
| `sp` | spinels |
| `carb` | carbonates |
| `ilhem` | ilmenites and hematites |
| `spr` | sapphirines |
| `osm` | osumilites |
| `stp` | stilpnomelanes |
| `pmp` | pumpellyites |
| `pre` | prehnites |

填写第 2 行时必须从上表选择与实测矿物相对应的代码。例如：长石使用 `fsp`，石榴子石使用 `g`，单斜辉石使用 `cpx`。

## TXT 转 Excel：输入说明

使用“TXT 转 Excel”时，请选择 AX-Win 输出的 `tab.txt` 文件。

## 系统要求

- Windows 操作系统

## 文件校验

`v1.0.0` 版本的 SHA-256：

```text
0FB0DFAB6893EC081BCBC5AEB2D798DA50D4A3A6D112B2333FAB244C75203FFD  EPMA数据转换.exe
0FB0DFAB6893EC081BCBC5AEB2D798DA50D4A3A6D112B2333FAB244C75203FFD  EPMA.exe
```

仓库同时提供 `SHA256SUMS.txt`，可用于核对下载文件是否完整。

## Windows 安全提示

当前可执行文件尚未添加数字签名，因此 Windows SmartScreen 可能显示安全提醒。请确认下载来源为本仓库，并在运行前核对 SHA-256。

## 问题反馈

如遇到转换或使用问题，可以在本仓库的 [Issues](https://github.com/Cchuan-hcr/Cchuan./issues) 页面提交反馈。

## 许可证

本仓库暂未添加开源许可证。
